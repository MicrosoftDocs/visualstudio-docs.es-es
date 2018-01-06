---
title: "Solución (. Archivo sln) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- sln files, VSPackages
- solutions, .sln files
- .sln files, VSPackages
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ad918b72d38e61fb1670adda8ff1f730987c2aa3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="solution-sln-file"></a>Solución (. Archivo sln)
Una solución es una estructura para organizar los proyectos de Visual Studio. La solución mantiene la información de estado para los proyectos en .sln (basado en texto, compartido) y archivos .suo (opciones de solución binario, específica del usuario). Para obtener más información sobre .suo (archivos), consulte [opciones de usuario de la solución (. Archivo suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md).  
  
 Si se carga el VSPackage como resultado de la que se hace referencia en el archivo .sln, el entorno llama a <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> para leer en el archivo .sln.  
  
 El archivo .sln contiene información basado en texto que el entorno se usa para buscar y cargar los parámetros de nombre y valor de los datos persistentes y el proyecto de VSPackages que hace referencia. Cuando un usuario abre una solución, el entorno se recorre el `preSolution`, `Project`, y `postSolution` información en el archivo .sln para cargar la solución, los proyectos dentro de la solución y cualquier información guardada se adjunta a la solución.  
  
 Archivo de cada proyecto contiene información adicional leído por el entorno para rellenar la jerarquía de elementos de ese proyecto. La persistencia de datos de la jerarquía se controla mediante el proyecto; los datos no se almacenan normalmente en el archivo .sln, aunque puede escribir intencionadamente información del proyecto en el archivo .sln si opta por hacerlo. Para obtener más información relacionada con la persistencia, consulte [persistencia de un proyecto](../../extensibility/internals/project-persistence.md) y [abrir y guardar elementos de proyecto](../../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="solution-file-contents"></a>Contenido del archivo de solución  
 El archivo .sln consta de varias secciones, como se muestra en el código siguiente.  
  
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
  
1.  El entorno lee la sección Global del archivo .sln y procesa todas las secciones marcadas `preSolution`. En este caso, hay una instrucción:  
  
    ```  
    GlobalSection(SolutionConfiguration) = preSolution  
         ConfigName.0 = Debug  
         ConfigName.1 = Release  
    ```  
  
     Cuando se lee el entorno de la `GlobalSection('name')` etiqueta, asigna el nombre a un VSPackage mediante el registro. El nombre de clave debe existir en el registro bajo [HKLM\\< raíz del registro de Id. de la aplicación\>\SolutionPersistence\AggregateGUIDs]. Valor predeterminado de las claves es el GUID de paquete (REG_SZ) del VSPackage que ha escrito las entradas.  
  
2.  El entorno de carga de VSPackage, llamadas `QueryInterface` en VSPackage para la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> interfaz y las llamadas del <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> método con los datos en la sección para el VSPackage puede almacenar los datos. El entorno repite este proceso para cada `preSolution` sección.  
  
3.  El entorno recorre en iteración los bloques de persistencia de proyecto. En este caso, hay un proyecto.  
  
    ```  
    Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",  
    "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"  
    EndProject  
    ```  
  
     Esta instrucción contiene el GUID único del proyecto y el GUID del tipo de proyecto. Esta información es utilizada por el entorno para buscar el archivo de proyecto o archivos que pertenecen a la solución y el VSPackage necesarias para cada proyecto. El proyecto GUID se pasa a <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> para cargar el VSPackage específico relacionados con el proyecto, a continuación, se carga el proyecto por el VSPackage. En este caso, el VSPackage que se carga para este proyecto es Visual Basic.  
  
     Cada proyecto puede conservar un identificador de instancia único del proyecto para que se puede tener acceso según sea necesario en otros proyectos de la solución. Lo ideal es que, si la solución y los proyectos están bajo control de código fuente, debe ser la ruta de acceso al proyecto en relación con la ruta de acceso a la solución. Cuando se carga por primera vez la solución, los archivos de proyecto no pueden estar en el equipo del usuario. Si tiene el archivo de proyecto que se almacenan en el servidor en relación con el archivo de solución, es relativamente sencillo para el archivo de proyecto se encuentra y se copian en el equipo del usuario. A continuación, copia y carga el resto de los archivos necesarios para el proyecto.  
  
4.  Según la información contenida en la sección de proyecto del archivo .sln, carga el entorno de cada archivo de proyecto. El propio proyecto, a continuación, es responsable de rellenar la jerarquía del proyecto y cargar los proyectos anidados.  
  
5.  Una vez procesadas todas las secciones del archivo .sln, la solución se muestra en el Explorador de soluciones y está lista para su modificación por el usuario.  
  
 Si se produce un error en cualquier VSPackage que implemente un proyecto de la solución cargar, el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A> se llama al método y todos los otros proyectos de la solución se proporciona una oportunidad para omitir los cambios que podría haber realizado durante la carga. Si se producen errores de análisis, se conserva tanta información como sea posible con los archivos de solución y el entorno muestra un cuadro de diálogo advertir al usuario que la solución está dañada.  
  
 Cuando se guarda o se cierra, la solución el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A> método se llama y se pasa a la jerarquía para ver si se han realizado cambios a la solución que tienen que escribirse en el archivo .sln. Un valor null, pasado a `QuerySaveSolutionProps` en <xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS>, indica que se está mantiene información de la solución. Si el valor no es null, la información guardada es para un proyecto específico, determinado por el puntero a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfaz.  
  
 Si hay información que se guarda, la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> interfaz se denomina con un puntero a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A> método. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> , a continuación, se llama el método por el entorno para recuperar los pares de nombre-valor de `IPropertyBag` de interfaz y escribir la información en el archivo .sln.  
  
 `SaveSolutionProps`y `WriteSolutionProps` objetos se denominan de forma recursiva por el entorno para recuperar la información que deba guardarse de la `IPropertyBag` interfaz hasta que se han escrito todos los cambios en el archivo .sln. De esta manera, puede asegurarse de que la información se conservarán con la solución y disponible próxima vez que se abra la solución.  
  
 Se enumera cada VSPackage cargado para ver si tiene algo para guardar en archivo .sln. Es solo en tiempo de carga que se consultan las claves del registro. El entorno sabe acerca de todos los paquetes de carga porque están en memoria en el momento en que se guarda la solución.  
  
 Solo el archivo .sln contiene las entradas de la `preSolution` y `postSolution` secciones. No hay ningún secciones similar en el archivo .suo puesto que la solución necesita esta información para cargar correctamente. El archivo .suo contiene opciones específicas de usuario, como notas privadas, que no están diseñados para ser compartidos o colocado en el control de código fuente.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 [Opciones de usuario de la solución (. Archivo suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md)   
 [Soluciones](../../extensibility/internals/solutions.md)