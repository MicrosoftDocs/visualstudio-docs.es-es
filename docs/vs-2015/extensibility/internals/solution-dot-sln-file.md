---
title: Solución (. Sln) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- sln files, VSPackages
- solutions, .sln files
- .sln files, VSPackages
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d9e045ab707620fe985e34174238081f6168e5af
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154964"
---
# <a name="solution-sln-file"></a>Archivo de la solución (.Sln)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Una solución es una estructura para organizar los proyectos en Visual Studio. La solución mantiene la información de estado de los proyectos en archivos. sln (basados en texto, compartidos) y. suo (binario, opciones de solución específicas del usuario). Para obtener más información sobre los archivos. suo, vea opciones de usuario de la [solución (. Suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md).  
  
 Si el VSPackage se carga como resultado de hacer referencia al archivo. sln, el entorno llama <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> a para leer en el archivo. sln.  
  
 El archivo. sln contiene información basada en texto que utiliza el entorno para buscar y cargar los parámetros de nombre y valor de los datos persistentes y del proyecto VSPackages al que hace referencia. Cuando un usuario abre una solución, el entorno recorre la `preSolution` `Project` información, y `postSolution` en el archivo. sln para cargar la solución, los proyectos de la solución y cualquier información conservada asociada a la solución.  
  
 El archivo de cada proyecto contiene información adicional leída por el entorno para rellenar la jerarquía con los elementos de ese proyecto. El proyecto controla la persistencia de los datos de la jerarquía; Normalmente, los datos no se almacenan en el archivo. sln, aunque puede escribir intencionadamente la información del proyecto en el archivo. sln si decide hacerlo. Para obtener más información sobre la persistencia, vea [persistencia del proyecto](../../extensibility/internals/project-persistence.md) y [abrir y guardar elementos de proyecto](../../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="solution-file-contents"></a>Contenido del archivo de solución  
 El archivo. sln se compone de varias secciones, como se muestra en el código siguiente.  
  
```  
Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1", "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"  
EndProject  
Global  
  GlobalSection(SolutionNotes) = postSolution  
  EndGlobalSection  
  GlobalSection(SolutionConfiguration) = preSolution  
       ConfigName.0 = Debug  
       ConfigName.1 = Release  
  EndGlobalSection  
  GlobalSection(ProjectDependencies) = postSolution  
  EndGlobalSection  
  GlobalSection(ProjectConfiguration) = postSolution  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.ActiveCfg = Debug|x86  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.Build.0 = Debug|x86  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.ActiveCfg = Release|x86  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.Build.0 = Release|x86  
  EndGlobalSection  
  GlobalSection(ExtensibilityGlobals) = postSolution  
  EndGlobalSection  
  GlobalSection(ExtensibilityAddIns) = postSolution  
  EndGlobalSection  
EndGlobal  
```  
  
 Para cargar una solución, el entorno realiza la siguiente secuencia de tareas.  
  
1. El entorno lee la sección global del archivo. sln y procesa todas las secciones marcadas como `preSolution` . En este caso, hay una instrucción de este tipo:  
  
   ```  
   GlobalSection(SolutionConfiguration) = preSolution  
        ConfigName.0 = Debug  
        ConfigName.1 = Release  
   ```  
  
    Cuando el entorno lee la `GlobalSection('name')` etiqueta, asigna el nombre a un VSPackage mediante el registro. El nombre de clave debe existir en el registro en [HKLM \\<Application ID. de la raíz del registro \> \SolutionPersistence\AggregateGUIDs]. El valor predeterminado de las claves es el GUID del paquete (REG_SZ) del VSPackage que escribió las entradas.  
  
2. El entorno carga el VSPackage, llama a `QueryInterface` en el VSPackage de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> interfaz y llama al <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> método con los datos de la sección para que el VSPackage pueda almacenar los datos. El entorno repite este proceso para cada `preSolution` sección.  
  
3. El entorno recorre en iteración los bloques de persistencia del proyecto. En este caso, hay un proyecto.  
  
   ```  
   Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",  
   "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"  
   EndProject  
   ```  
  
    Esta instrucción contiene el GUID del proyecto único y el GUID del tipo de proyecto. El entorno usa esta información para buscar el archivo o los archivos de proyecto que pertenecen a la solución y el VSPackage necesario para cada proyecto. El GUID del proyecto se pasa a <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> para cargar el VSPackage concreto relacionado con el proyecto y, a continuación, el VSPackage carga el proyecto. En este caso, el VSPackage que se carga para este proyecto es Visual Basic.  
  
    Cada proyecto puede conservar un identificador de instancia de proyecto único para que otros proyectos de la solución puedan tener acceso a él según sea necesario. Idealmente, si la solución y los proyectos están bajo control de código fuente, la ruta de acceso al proyecto debe ser relativa a la ruta de acceso a la solución. La primera vez que se carga la solución, los archivos del proyecto no pueden estar en el equipo del usuario. Al tener el archivo de proyecto almacenado en el servidor en relación con el archivo de solución, es relativamente sencillo que el archivo de proyecto se encuentre y copie en el equipo del usuario. Después, copia y carga el resto de los archivos necesarios para el proyecto.  
  
4. En función de la información contenida en la sección Project del archivo. sln, el entorno carga cada archivo de proyecto. El propio proyecto es responsable de rellenar la jerarquía del proyecto y cargar los proyectos anidados.  
  
5. Una vez procesadas todas las secciones del archivo. sln, la solución se muestra en Explorador de soluciones y está lista para ser modificada por el usuario.  
  
   Si se produce un error al cargar cualquier VSPackage que implementa un proyecto en la solución, se <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A> llama al método y cada otro proyecto de la solución tiene la oportunidad de omitir los cambios que podría haber realizado durante la carga. Si se producen errores de análisis, la cantidad de información posible se conserva con los archivos de la solución y el entorno muestra un cuadro de diálogo que advierte al usuario de que la solución está dañada.  
  
   Cuando la solución se guarda o se cierra, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A> se llama al método y se pasa a la jerarquía para ver si se han realizado cambios en la solución que deben especificarse en el archivo. sln. Un valor null, que se pasa a `QuerySaveSolutionProps` en <xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS> , indica que la información se conserva para la solución. Si el valor no es null, la información persistente es para un proyecto específico, determinado por el puntero a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfaz.  
  
   Si hay información que se va a guardar, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> se llama a la interfaz con un puntero al <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A> método. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A>A continuación, el entorno llama al método para recuperar los pares de nombre y valor de la `IPropertyBag` interfaz y escribir la información en el archivo. sln.  
  
   `SaveSolutionProps``WriteSolutionProps`el entorno llama recursivamente a los objetos y para recuperar información que se va a guardar desde la `IPropertyBag` interfaz hasta que todos los cambios se hayan introducido en el archivo. sln. De este modo, puede asegurarse de que la información se conservará con la solución y estará disponible la próxima vez que se abra la solución.  
  
   Cada VSPackage cargado se enumera para ver si tiene algo que guardar en el archivo. sln. Solo es en el momento de la carga que se consultan las claves del registro. El entorno conoce todos los paquetes cargados porque están en memoria en el momento en que se guarda la solución.  
  
   Solo el archivo. sln contiene entradas en las `preSolution` `postSolution` secciones y. No hay secciones similares en el archivo. suo, ya que la solución necesita esta información para cargar correctamente. El archivo. suo contiene opciones específicas del usuario, como notas privadas, que no están diseñadas para ser compartidas o colocadas bajo control de código fuente.  
  
## <a name="see-also"></a>Consulte también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 [Opciones de usuario de la solución (. Suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md)   
 [Soluciones](../../extensibility/internals/solutions-overview.md)
