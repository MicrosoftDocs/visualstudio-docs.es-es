---
title: Solución (. Los archivos sln) | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- sln files, VSPackages
- solutions, .sln files
- .sln files, VSPackages
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 737186560f6e1cde0fc35d16dab35fb146685fbb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47578624"
---
# <a name="solution-sln-file"></a>Archivo de la solución (.Sln)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [solución (. Los archivos sln)](https://docs.microsoft.com/visualstudio/extensibility/internals/solution-dot-sln-file).  
  
Una solución es una estructura para organizar los proyectos en Visual Studio. La solución mantiene la información de estado para los proyectos de .sln (basado en texto, compartido) y archivos .suo (opciones de solución binarios específicos del usuario). Para obtener más información sobre .suo (archivos), consulte [opciones de usuario de la solución (. Archivo suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md).  
  
 Si se carga el VSPackage como resultado de la que se hace referencia en el archivo .sln, el entorno llama a <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> para leer el archivo .sln.  
  
 El archivo .sln contiene información basado en texto que el entorno usa para buscar y cargar los parámetros de nombre y valor para los datos persistentes y el proyecto de VSPackages que hace referencia. Cuando un usuario abre una solución, el entorno se recorre el `preSolution`, `Project`, y `postSolution` información en el archivo .sln para cargar la solución, los proyectos dentro de la solución y cualquier información persistente asociado a la solución.  
  
 Cada archivo del proyecto contiene información adicional, lea el entorno para rellenar la jerarquía de elementos de ese proyecto. La persistencia de datos de la jerarquía se controla mediante el proyecto; los datos no se almacenan normalmente en el archivo .sln, aunque puede escribir intencionadamente información del proyecto en el archivo .sln si opta por hacerlo. Para obtener más información sobre persistencia, consulte [persistencia de un proyecto](../../extensibility/internals/project-persistence.md) y [abriendo y guardando elementos de proyecto](../../extensibility/internals/opening-and-saving-project-items.md).  
  
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
  
     Cuando se lee el entorno de la `GlobalSection('name')` etiqueta, asigne el nombre de un VSPackage mediante el registro. El nombre de clave debe existir en el registro en [HKLM\\< raíz del registro de Id. de aplicación\>\SolutionPersistence\AggregateGUIDs]. Valor predeterminado de las claves es el GUID de paquete (REG_SZ) del VSPackage que ha escrito las entradas.  
  
2.  El entorno de carga de VSPackage, llamadas `QueryInterface` en el VSPackage para el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> interfaz y llama a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> método con los datos en la sección para el VSPackage puede almacenar los datos. El entorno de este proceso repite para cada `preSolution` sección.  
  
3.  El entorno se itera por los bloques de persistencia del proyecto. En este caso, hay un proyecto.  
  
    ```  
    Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",  
    "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"  
    EndProject  
    ```  
  
     Esta instrucción contiene el GUID único del proyecto y el GUID del tipo de proyecto. Esta información se usa el entorno para buscar el archivo de proyecto o archivos que pertenecen a la solución, y el VSPackage necesarias para cada proyecto. El proyecto se pasa el GUID al <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> para cargar el VSPackage específico relacionados con el proyecto, el proyecto se carga el VSPackage. En este caso, el VSPackage que se carga para este proyecto es Visual Basic.  
  
     Cada proyecto puede almacenar un identificador de instancia único del proyecto para que se puede tener acceso al según sea necesario para otros proyectos de la solución. Lo ideal es que, si la solución y proyectos están bajo control de código fuente, la ruta de acceso para el proyecto debe ser relativa a la ruta de acceso a la solución. Cuando se carga la solución por primera vez, los archivos de proyecto no pueden estar en el equipo del usuario. Al tener el archivo de proyecto almacenado en el servidor en relación con el archivo de solución, es relativamente sencillo para el archivo de proyecto para encontrar y copiar en el equipo del usuario. A continuación, copia y carga el resto de los archivos necesarios para el proyecto.  
  
4.  Según la información contenida en la sección de proyecto del archivo .sln, el entorno de carga cada archivo del proyecto. El propio proyecto, a continuación, es responsable de rellenar la jerarquía del proyecto y cargar los proyectos anidados.  
  
5.  Una vez procesadas todas las secciones del archivo .sln, la solución se muestra en el Explorador de soluciones y está lista para su modificación por el usuario.  
  
 Si no se puede cargar, cualquier VSPackage que implemente un proyecto de la solución el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A> se llama al método y todos los proyectos de la solución tiene la oportunidad para pasar por alto los cambios haya realizado durante la carga. Si se producen errores de análisis, se conserva toda la información como sea posible con los archivos de solución y el entorno muestra un cuadro de diálogo que advierte al usuario que la solución está dañada.  
  
 Cuando se guarda o se cierra, la solución el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A> método se llama y se pasa a la jerarquía para ver si se han realizado cambios a la solución que tienen que escribirse en el archivo .sln. Un valor null, pasado a `QuerySaveSolutionProps` en <xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS>, indica que es que se va a conservar información para la solución. Si el valor no es null, la información guardada es para un proyecto específico, determinado por el puntero a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfaz.  
  
 Si no hay información que podría ahorrarse el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> interfaz se denomina con un puntero a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A> método. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> , a continuación, se llama al método por el entorno para recuperar los pares de nombre-valor de `IPropertyBag` interfaz y escribir la información en el archivo .sln.  
  
 `SaveSolutionProps` y `WriteSolutionProps` objetos se denominan de forma recursiva el entorno para recuperar la información que deba guardarse del `IPropertyBag` hasta que se han escrito todos los cambios en el archivo .sln de la interfaz. De este modo, puede asegurarse de que se conservarán la información con la solución y disponible la próxima vez que se abra la solución.  
  
 Para ver si tiene algo para guardar en archivo .sln, se enumera cada VSPackage cargado. Es solo en tiempo de carga que se consultan las claves del registro. El entorno sabe acerca de todos los paquetes de cargados porque se encuentran en memoria en el momento en que se guarda la solución.  
  
 Solo el archivo .sln contiene entradas en el `preSolution` y `postSolution` secciones. No hay ningún secciones similar en el archivo .suo, ya que la solución debe esta información para cargar correctamente. El archivo .suo contiene opciones específicas del usuario, como notas privadas, que no están diseñadas para ser compartidos o situados bajo control de código fuente.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 [Opciones de usuario de la solución (. Archivo suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md)   
 [Soluciones](../../extensibility/internals/solutions.md)

