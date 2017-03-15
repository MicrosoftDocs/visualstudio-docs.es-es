---
title: "Componentes principales de modelo de proyecto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "interfaces, objetos y modelos de proyecto"
  - "modelos de proyecto, servicios"
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Componentes principales de modelo de proyecto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Las tablas siguientes expanda en el modelo de proyecto.  Las actuales descripciones breves de las tablas de las interfaces y los servicios identificados en el modelo, y las interfaces y los servicios asociados con los objetos específicos.  Además, las tablas detallan otras interfaces que sean opcionales en la creación y el mantenimiento del proyecto dependiendo de los requisitos de tipo de proyecto específico.  
  
 Para obtener más información, vea [Compatibilidad con herramientas de exploración de símbolos](../../extensibility/internals/supporting-symbol-browsing-tools.md).  
  
### Objeto de paquete  
  
|Interfaz|Comentarios|  
|--------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|Inicializa un VSPackage en el IDE y colocar sus servicios a disposición del IDE.|  
  
### Objeto de generador de proyecto  
  
|Interfaz|Comentarios|  
|--------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|Administra crear nuevos proyectos y proyectos existentes que abra.|  
  
### Objetos del proyecto  
  
|Interfaces|Comentarios|  
|----------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|Administra la adición y eliminación de elementos de proyecto, abra los editores, y mantiene la asignación entre cada moniker del documento y `VSITEMID`.  hereda de `IVsProject` y de `IVsProject2`.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|Administra las propiedades de navegación y presentación y proporciona eventos.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|Permite la ejecución de comandos similar a la de `IOleCommandTarget` para los comandos como cortar y Rename que sólo se aplican cuando el foco esté en el explorador de soluciones.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Actúa como interfaz de destino primario de comando para una jerarquía del proyecto.  Es la interfaz estándar para ver los objetos para el estado del comando o estado y comandos en ejecución.  Disponibles cuando no se centran en la ventana del proyecto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Coordina la persistencia del estado del proyecto.  Normalmente, se almacena como un archivo de proyecto pero puede ser adecuado al estado a los sistemas de almacenamiento que no están basadas en archivos.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|Permite al proyecto de administrar todos los aspectos de persistencia para los elementos de proyecto, como archivos en disco o objetos en otros sistemas de almacenamiento.  la interfaz de `IVsPeristHierarchyItem2` se utiliza para los elementos que no implementan la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Coordina las interacciones con el control de código fuente.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|Proyectos de administrar la información de configuración.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|Administra objetos de configuración del proyecto, como configuraciones debug y release.  Compilación, implementar, y las operaciones de depuración se coordinan mediante objetos de configuración del proyecto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|Implementado por jerarquías para controlar la cancelación \(destructiva\) o quitar las opciones \(no destructivas\) para los elementos de la jerarquía.  Llame a la interfaz de consulta en la interfaz de `IVsHierarchyDeleteHandler` de la interfaz de `IVsHierarchy` .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|Proporciona la opción de implementación de que el objeto que admite la interfaz de `IVsCfgProvider2` en una identidad diferente COM que el objeto de proyecto que implementa la interfaz de `IVsHierarchy` .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|Interfaz opcional implementada para hacer el proyecto extensible por otros desarrolladores.  La interfaz de `IVsProjectStartupServices` permite a un Paquete de terceros para registrar un GUID que se conserva en el archivo de proyecto para cada vez que se carga el proyecto, se carga el servicio de terceros GUID en el archivo de proyecto y la llamada `QueryService` para ese GUID.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|Implementado por jerarquías de origen en una ventana de `UIHierarchy` para coordinar operaciones del portapapeles como cortar, copiar, pegar y.  Utilice la interfaz de `AdviseClipboardHelperEvents` para registrar eventos del portapapeles.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|Proporciona información sobre un elemento arrastrado en relación con el origen de datos durante una operación de arrastrar y colocar en una ventana jerarquía de la interfaz de usuario.  Nombre de la interfaz de `IVsHierarchy` .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|Proporciona información sobre un elemento arrastrado relativa a su destino durante una operación de arrastrar y colocar en una ventana jerarquía de la interfaz de usuario.  Nombre de la interfaz de `IVsHierarchy` .|  
  
### Objeto Configuration.  
  
|Interfaces|Comentarios|  
|----------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|Proporciona información sobre una configuración.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|Proyectos de administrar la información de configuración.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|Habilita un proyecto se ejecuten bajo el control del depurador.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|Implementado por los proyectos de implementación que realizan las operaciones de implementación para otros proyectos.|  
  
### Objeto de generador de configuración  
  
|Interfaces|Comentarios|  
|----------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|Administra la operación de compilación de una configuración del proyecto.|  
  
### Objetos adicionales del proyecto  
  
|Interfaces|Comentarios|  
|----------------|-----------------|  
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|Muestra propiedades de elementos en la ventana de **Propiedades** .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|Resultados de muestra para la implementación.|  
  
 La tabla siguiente muestra las descripciones breves de servicios identificados en el modelo de proyecto.  
  
### Servicios  
  
|Servicio|Comentarios|  
|--------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|Utilizado por VSPackages que implementa tipos de proyecto para registrar que el generador de proyectos existe con el IDE.  El Paquete debe llamar a `QueryService` para este servicio y registrar el generador del proyecto cuando se llama al método de `IVsPackage::SetSite` .  Si el método de `SetSite` no se denomina, no se crea instancias.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Proporciona acceso al IDE interno, noción integrada de la solución actual, como la capacidad de enumerar proyectos, crear nuevos proyectos, toma el aviso del proyecto, y así sucesivamente.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|Llamado por los proyectos que desea participar en el control de código fuente.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|Mantiene una tabla de documentos abiertos para determinar si se abren uno o más elementos de proyecto ya.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|Contiene las interfaces y los métodos denominados para abrir realmente un elemento de proyecto utilizando el editor estándar o un editor específico.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|Necesario para llamar a todos los proyectos cuando agregue, quite o cambie sus elementos.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|Administra los cambios a un archivo o un directorio y notifica a clientes cuando los archivos seleccionados se han cambiado en el disco.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|Necesario para llamar a todos los proyectos y editores antes de que los elementos modificados o los guardarán.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|Administra el orden de las operaciones de compilación e implementación de las configuraciones de proyecto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|Proporciona acceso a los servicios de bajo nivel de depurador utilizados para la mayoría de los controles de depuración.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|Acceso de VSPackages de permisos a la información sobre selecciones actuales y la comunicación de los permisos con la ventana de **Propiedades** .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Proporciona la funcionalidad Interfaz de usuario\-relacionada básica del IDE, como la capacidad de crear y de mostrar las ventanas de herramientas o las ventanas de documento o de notificar un error al usuario.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|Proporciona acceso a la barra de estado del IDE.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|Se utiliza para implementar el modelo de automatización.  En el modelo de proyecto, se devolverá un objeto de propiedades que permiten crear una instancia de ese objeto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|Se utiliza para implementar eventos del portapapeles en el objeto de proyecto en la jerarquía.  `SVsUIHierWinClipboardHelper` permite correcto de cortar, copiar, y las operaciones de pegar.|  
  
## Vea también  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Lista de comprobación: Crear nuevos tipos de proyecto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Not in Build: Using HierUtil7 Project Classes to Implement a Project Type \(C\+\+\)](http://msdn.microsoft.com/es-es/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [Compatibilidad con herramientas de exploración de símbolos](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Elementos de un modelo de proyecto](../../extensibility/internals/elements-of-a-project-model.md)