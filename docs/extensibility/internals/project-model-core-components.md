---
title: Componentes principales del modelo de proyecto | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project models, objects and interfaces
- project models, services
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2cfb9db9c354eb4c10ece0f5a8259f3d4a104e28
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133139"
---
# <a name="project-model-core-components"></a>Componentes principales del proyecto de modelo
Las siguientes tablas se expanden en el modelo de proyecto. Las tablas ofrecen descripciones breves de las interfaces y los servicios identificados en el modelo y las interfaces y los servicios asociados a objetos específicos. Además, las tablas detallan otras interfaces que son opcionales en la creación del proyecto y el mantenimiento según los requisitos de su tipo de proyecto específico.  
  
 Para obtener más información, consulte [herramientas de exploración de admitir símbolo](../../extensibility/internals/supporting-symbol-browsing-tools.md).  
  
### <a name="package-object"></a>Objeto de paquete  
  
|Interfaz|Comentarios|  
|---------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|Inicializa un VSPackage en el IDE y hace que sus servicios estén disponibles para el IDE.|  
  
### <a name="project-factory-object"></a>Objeto de generador de proyectos  
  
|Interfaz|Comentarios|  
|---------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|Administra la creación de nuevos proyectos y abrir proyectos existentes.|  
  
### <a name="project-objects"></a>Objetos de proyecto  
  
|Interfaces|Comentarios|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|Administra la adición y eliminación de elementos de proyecto, se abre editores y mantiene la asignación entre cada moniker del documento y el `VSITEMID`. Hereda de `IVsProject` y `IVsProject2`.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|Administra las propiedades de navegación y la presentación y proporciona eventos.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|Habilita el comando ejecución similar de `IOleCommandTarget` para comandos como cortar y cambiar el nombre que se aplican solo cuando el foco está en el Explorador de soluciones.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Actúa como la interfaz de destino del comando principal para una jerarquía de proyectos. Es la interfaz estándar para consultar objetos para sus comandos de estado o el estado y la ejecución del comando. Está disponible cuando no se centra en la ventana del proyecto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Coordina la persistencia del estado del proyecto. Normalmente, el estado del proyecto se almacena como un archivo de proyecto, pero puede adaptarse a sistemas de almacenamiento que no están basados en archivos.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|Permite que el proyecto administrar todos los aspectos de persistencia para los elementos de proyecto, como archivos en disco o los objetos en otros sistemas de almacenamiento. El `IVsPeristHierarchyItem2` interfaz se utiliza para los elementos que no implementan la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> interfaz.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Coordina las interacciones con control de código fuente.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|Permite administrar la información de configuración de los proyectos.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|Administra los objetos de configuración de proyecto, como las configuraciones de depuración y lanzamiento. Generar, implementar y depurar las operaciones son coordinadas a través de objetos de configuración de proyecto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|Implementa las jerarquías para controlar la eliminación (destructiva) o quitar opciones (no destructiva) para los elementos de la jerarquía. Llamar a la interfaz de consulta en el `IVsHierarchyDeleteHandler` de la interfaz de la `IVsHierarchy` interfaz.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|Proporciona la opción de implementación de tener el objeto que admite la `IVsCfgProvider2` interfaz en una identidad de COM diferente que el objeto de proyecto que implementa el `IVsHierarchy` interfaz.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|Interfaz opcional que se implementan para hacer que el proyecto extensible por otros desarrolladores. El `IVsProjectStartupServices` interfaz permite que un VSPackage de terceros registrar un GUID que se mantendrán en el archivo de proyecto para que cada vez que se cargue el proyecto, cargar el servicio de terceros GUID en el archivo de proyecto y llame a `QueryService` para ese GUID.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|Implementado en las jerarquías de origen en un `UIHierarchy` ventana para coordinar las operaciones del Portapapeles como cortar, copiar y pegar. Use la `AdviseClipboardHelperEvents` interfaz para registrar eventos del Portapapeles.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|Proporciona información sobre un elemento arrastrado en relación con su origen de datos durante una operación de arrastrar y colocar en una ventana de la jerarquía de interfaz de usuario. Llamar desde el `IVsHierarchy` interfaz.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|Proporciona información sobre un elemento arrastrado con respecto a su destino de colocación durante una operación de arrastrar y colocar en una ventana de la jerarquía de interfaz de usuario. Llamar desde el `IVsHierarchy` interfaz.|  
  
### <a name="configuration-object"></a>Objeto de configuración  
  
|Interfaces|Comentarios|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|Proporciona información acerca de una configuración.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|Permite administrar la información de configuración de los proyectos.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|Permite a un proyecto para ejecutarse bajo el control del depurador.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|Implementa los proyectos de implementación que realizan operaciones de implementación para otros proyectos.|  
  
### <a name="configuration-builder-object"></a>Objeto de generador de configuración  
  
|Interfaces|Comentarios|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|Administra la operación de generación de una configuración del proyecto.|  
  
### <a name="additional-project-objects"></a>Objetos de proyecto adicionales  
  
|Interfaces|Comentarios|  
|----------------|--------------|  
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|Muestra de elemento de propiedades en el **propiedades** ventana.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|Salidas de muestra para la implementación.|  
  
 En la tabla siguiente presenta breves descripciones de los servicios identificados en el modelo de proyecto.  
  
### <a name="services"></a>Servicios  
  
|web de Office|Comentarios|  
|-------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|Usar VSPackages que implementan tipos de proyecto para registrar que el generador de proyectos existe con el IDE. El VSPackage debe llamar a `QueryService` para este servicio y registrar la fábrica de su proyecto cuando `IVsPackage::SetSite` se llama al método. Si el `SetSite` no se llama a método, no se crea una instancia de su proyecto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Proporciona acceso a la noción interno, integrado del IDE de la solución actual, como la capacidad para enumerar los proyectos, crear nuevos proyectos, tomar nota de los cambios en el proyecto y así sucesivamente.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|Llamado por los proyectos que desean participar en el control de código fuente.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|Mantiene una tabla de documentos abiertos para determinar si uno o varios de sus elementos de proyecto ya están abiertos.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|Contiene las interfaces y métodos utilizados para un elemento de proyecto con el editor estándar o un editor concreto en realidad podemos abrir.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|Debe llamarse en todos los proyectos al que agregar, quitar o cambiar el nombre de sus elementos.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|Administra los cambios realizados en un archivo o directorio y notifica a los clientes si los archivos seleccionados se han cambiado en el disco.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|Se requiere para ser llamado por todos los proyectos y editores desfasadas elementos o guardarlos.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|Administra el orden de las operaciones de compilación e implementación para las configuraciones de proyecto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|Proporciona acceso a los servicios de bajo nivel depurador utilizados para la mayoría de los controles depuración.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|Permite el acceso de VSPackages para obtener información acerca de las selecciones actuales y permite la comunicación con el **propiedades** ventana.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Proporciona funcionalidad básica de IDE relacionadas con la interfaz de usuario, como la capacidad para crear y enumerar las ventanas de herramientas o las ventanas de documento o para notificar un error al usuario.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|Proporciona acceso a la barra de estado del IDE.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|Se utiliza para implementar el modelo de automatización. En el modelo de proyecto, devolverá un objeto de propiedades que le permite crea una instancia de ese objeto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|Se utiliza para implementar los eventos de Portapapeles en el objeto de proyecto de la jerarquía. `SVsUIHierWinClipboardHelper` permite correctamente identificador operaciones de cortar, copiar y pegar.|  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Lista de comprobación: Creación de nuevos tipos de proyecto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [No en la compilación: usar clases de proyectos de HierUtil7 para implementar un tipo de proyecto (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [Compatibilidad con herramientas de exploración de símbolos](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Elementos de un modelo de proyecto](../../extensibility/internals/elements-of-a-project-model.md)