---
title: "Soluci&#243;n (. Archivo sln) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SLN (archivos), VSPackages"
  - "soluciones, .sln (archivos)"
  - ".sln (archivos), VSPackages"
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Soluci&#243;n (. Archivo sln)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Una solución es una estructura para organizar los proyectos en Visual Studio. La solución mantiene la información de estado para los proyectos de .sln \(basado en texto, compartido\) y archivos .suo \(opciones de solución binarios específicos del usuario\). Para obtener más información sobre .suo \(archivos\), consulte [Opciones de usuario de solución \(. Archivo suo\)](../../extensibility/internals/solution-user-options-dot-suo-file.md).  
  
 Si se carga el VSPackage como resultado que se hace referencia en el archivo .sln, el entorno llama a <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> para leer el archivo .sln.  
  
 El archivo .sln contiene información basado en texto que el entorno se utiliza para buscar y cargar los parámetros de nombre y valor de los datos conservados y el proyecto VSPackages hace referencia. Cuando un usuario abre una solución, el entorno se recorre el `preSolution`, `Project`, y `postSolution` información en el archivo .sln para cargar la solución, los proyectos dentro de la solución, y cualquier información almacenada conectados a la solución.  
  
 Archivo de cada proyecto contiene información adicional leído por el entorno para rellenar la jerarquía de elementos del proyecto. La persistencia de datos de la jerarquía se controla mediante el proyecto; los datos no se almacenan normalmente en el archivo .sln, aunque puede escribir intencionadamente información del proyecto en el archivo .sln si decide hacerlo. Para obtener más información relacionada con la persistencia, consulte [Persistencia de un proyecto](../../extensibility/internals/project-persistence.md) y [Abrir y guardar elementos de proyecto](../../extensibility/internals/opening-and-saving-project-items.md).  
  
## Contenido del archivo de solución  
 El archivo .sln consta de varias secciones, como se muestra en el código siguiente.  
  
```  
Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1", "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}" EndProject Global GlobalSection(SolutionNotes) = postSolution EndGlobalSection GlobalSection(SolutionConfiguration) = preSolution ConfigName.0 = Debug ConfigName.1 = Release EndGlobalSection GlobalSection(ProjectDependencies) = postSolution EndGlobalSection GlobalSection(ProjectConfiguration) = postSolution {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.ActiveCfg = Debug|x86 {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.Build.0 = Debug|x86 {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.ActiveCfg = Release|x86 {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.Build.0 = Release|x86 EndGlobalSection GlobalSection(ExtensibilityGlobals) = postSolution EndGlobalSection GlobalSection(ExtensibilityAddIns) = postSolution EndGlobalSection EndGlobal  
```  
  
 Para cargar una solución, el entorno realiza la siguiente secuencia de tareas.  
  
1.  El entorno lee la sección Global del archivo .sln y procesa todas las secciones marcadas `preSolution`. En este caso, hay una instrucción:  
  
    ```  
    GlobalSection(SolutionConfiguration) = preSolution ConfigName.0 = Debug ConfigName.1 = Release  
    ```  
  
     Cuando se lee el entorno de la `GlobalSection('name')` etiqueta, asigna el nombre a un VSPackage mediante el registro. El nombre de clave debe existir en el registro bajo \[\\SolutionPersistence\\AggregateGUIDs HKLM\\ \< raíz de aplicación Id. del registro \>\]. Valor predeterminado de las claves es el GUID del paquete \(REG\_SZ\) del VSPackage que escribió las entradas.  
  
2.  El entorno de carga de VSPackage, llamadas `QueryInterface` en el paquete VSPackage para el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> interfaz y llama el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> método con los datos en la sección VSPackage puede almacenar los datos. El entorno repite este proceso para cada `preSolution` sección.  
  
3.  El entorno se itera a través de los bloques de persistencia del proyecto. En este caso, hay un proyecto.  
  
    ```  
    Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1", "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}" EndProject  
    ```  
  
     Esta instrucción contiene el GUID único del proyecto y el GUID del tipo de proyecto. Esta información se utiliza en el entorno para buscar el archivo de proyecto o los archivos que pertenecen a la solución y el VSPackage necesarias para cada proyecto. El proyecto de GUID que se pasa a <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> para cargar el VSPackage específico relacionados con el proyecto, el proyecto se carga por el VSPackage. En este caso, el paquete VSPackage que se carga para este proyecto es de Visual Basic.  
  
     Cada proyecto puede conservar un identificador de instancia único del proyecto para que se puede tener acceso según sea necesario para otros proyectos de la solución. Idealmente, si la solución y los proyectos están bajo control de código fuente, la ruta de acceso al proyecto debe ser relativa a la ruta de acceso a la solución. Cuando se carga la solución por primera vez, los archivos de proyecto no pueden estar en el equipo del usuario. Al tener el archivo de proyecto que se almacenan en el servidor en relación con el archivo de solución, es relativamente sencillo para el archivo de proyecto se encuentra y se copia en el equipo del usuario. A continuación, copia y carga el resto de los archivos necesarios para el proyecto.  
  
4.  Según la información contenida en la sección del archivo .sln de proyecto, el entorno de carga cada archivo de proyecto. El propio proyecto es responsable de rellenar la jerarquía del proyecto y cargar los proyectos anidados.  
  
5.  Después de procesan todas las secciones del archivo .sln, la solución se muestra en el Explorador de soluciones y está lista para su modificación por el usuario.  
  
 Si cualquier VSPackage que implemente un proyecto de la solución no se carga, el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A> se llama al método y tiene la oportunidad de omitir los cambios haya realizado durante la carga de todos los proyectos de la solución. Si se producen errores de análisis, se conserva toda la información posible con los archivos de solución y el entorno muestra un cuadro de diálogo de advertencia al usuario que la solución está dañada.  
  
 Cuando se guarda o se cierra, la solución el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A> se llama el método y se pasa a la jerarquía para ver si se han realizado cambios a la solución que deben escribirse en el archivo .sln. Un valor null, que se pasa al `QuerySaveSolutionProps` en <xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS>, indica que se está conserva información para la solución. Si el valor no es null, la información almacenada es para un proyecto específico, determinado por el puntero de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfaz.  
  
 Si hay información que podría ahorrarse el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> interfaz se denomina con un puntero a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A> \(método\). El <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> a continuación, se llama el método por el entorno para recuperar los pares de nombre y valor de `IPropertyBag` de interfaz y escribir la información en el archivo .sln.  
  
 `SaveSolutionProps` y `WriteSolutionProps` objetos se denominan de forma recursiva por el entorno para recuperar información de guardar desde el `IPropertyBag` hasta que se han escrito todos los cambios en el archivo .sln de la interfaz. De esta forma, puede asegurarse de que se conservarán la información con la solución y disponible la próxima vez que se abra la solución.  
  
 Se enumera cada VSPackage cargado para ver si tiene algo para guardar el archivo .sln. Es solo en tiempo de carga que se consultan las claves del registro. El entorno sabe acerca de todos los paquetes de cargados porque están en memoria en el momento en que se guarda la solución.  
  
 Sólo el archivo .sln contiene entradas de la `preSolution` y `postSolution` secciones. No hay ninguna secciones similares en el archivo .suo puesto que la solución necesita esta información para cargar correctamente. El archivo .suo contiene opciones específicas de usuario, como notas privadas, que no están pensados para ser compartidos o bajo control de código fuente.  
  
## Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 [Opciones de usuario de solución \(. Archivo suo\)](../../extensibility/internals/solution-user-options-dot-suo-file.md)   
 [Soluciones](../../extensibility/internals/solutions.md)