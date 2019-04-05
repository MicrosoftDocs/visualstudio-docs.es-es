---
title: Componentes principales del modelo de proyecto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project models, objects and interfaces
- project models, services
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 30ec67e1e58e0c546c70ecb87841293161463b1b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58988732"
---
# <a name="project-model-core-components"></a>Componentes principales del modelo de proyecto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Las siguientes tablas se expanden en el modelo de proyecto. Las tablas ofrecen descripciones breves de las interfaces y los servicios identificados en el modelo y las interfaces y los servicios asociados a objetos específicos. Además, las tablas detallan otras interfaces que son opcionales en la creación del proyecto y el mantenimiento según los requisitos de su tipo de proyecto específico.  
  
 Para obtener más información, consulte [herramientas de exploración de símbolos que admiten](../../extensibility/internals/supporting-symbol-browsing-tools.md).  
  
### <a name="package-object"></a>Objeto de paquete  
  
|Interfaz|Comentarios|  
|---------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|Inicializa un VSPackage en el IDE y hace que sus servicios estén disponibles en el IDE.|  
  
### <a name="project-factory-object"></a>Objeto de generador de proyecto  
  
|Interfaz|Comentarios|  
|---------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|Administra la creación de nuevos proyectos y abrir proyectos existentes.|  
  
### <a name="project-objects"></a>Objetos de proyecto  
  
|Interfaces|Comentarios|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|Administra la adición y eliminación de elementos de proyecto, abre los editores y mantiene la asignación entre cada moniker del documento y el `VSITEMID`. Hereda de `IVsProject` y `IVsProject2`.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|Administra las propiedades de navegación y la presentación y proporciona eventos.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|Habilita comando ejecución similar de `IOleCommandTarget` para comandos como cortar y cambie el nombre que se aplican solo cuando el foco está en el Explorador de soluciones.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Sirve como la interfaz de destino del comando principal para una jerarquía de proyectos. Es la interfaz estándar para consultar objetos para los comandos de estado o estado y en ejecución del comando. Está disponible cuando no se centra en la ventana del proyecto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Coordina la persistencia del estado del proyecto. Normalmente, el estado del proyecto se almacena como un archivo de proyecto, pero se puede adaptar a sistemas de almacenamiento que no están basados en archivos.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|Permite que el proyecto administrar todos los aspectos de la persistencia de sus elementos de proyecto, como archivos en disco o los objetos en otros sistemas de almacenamiento. El `IVsPeristHierarchyItem2` interfaz se utiliza para los elementos que no implementan la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> interfaz.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Coordina las interacciones con el control de código fuente.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|Permite a los proyectos administren información de configuración.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|Administra los objetos de configuración de proyecto, como las configuraciones de depuración y lanzamiento. Crear, implementar y depurar las operaciones se coordina a través de los objetos de configuración del proyecto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|Implementado por jerarquías para controlar la eliminación (destrucción) o quitar (no destructiva) opciones para elementos de la jerarquía. Llamar a la interfaz de consulta en el `IVsHierarchyDeleteHandler` interfaz desde el `IVsHierarchy` interfaz.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|Proporciona la opción de implementación de tener el objeto que admite el `IVsCfgProvider2` interfaz en una identidad de COM diferente del objeto de proyecto que implementa el `IVsHierarchy` interfaz.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|Interfaz opcional implementada para hacer que su proyecto extensible por otros desarrolladores. El `IVsProjectStartupServices` interfaz permite que un VSPackage de otros fabricantes registrar un GUID que persisten en el archivo de proyecto para que cada vez que se carga el proyecto, cargar el GUID del servicio de terceros en el archivo de proyecto y llame a `QueryService` para ese GUID.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|Implementado por jerarquías de origen en un `UIHierarchy` ventana para coordinar las operaciones del Portapapeles como cortar, copiar y pegar. Use el `AdviseClipboardHelperEvents` interfaz para registrar los eventos del Portapapeles.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|Proporciona información sobre un elemento arrastrado en relación con su origen de datos durante una operación de arrastrar y colocar en una ventana de jerarquía de la interfaz de usuario. Se llama desde el `IVsHierarchy` interfaz.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|Proporciona información sobre un elemento arrastrado en relación con su destino de colocación durante una operación de arrastrar y colocar en una ventana de jerarquía de la interfaz de usuario. Se llama desde el `IVsHierarchy` interfaz.|  
  
### <a name="configuration-object"></a>Objeto de configuración  
  
|Interfaces|Comentarios|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|Proporciona información acerca de una configuración.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|Permite a los proyectos administren información de configuración.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|Habilita a un proyecto para ejecutarse bajo el control del depurador.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|Implementado por proyectos de implementación que realizan operaciones de implementación para otros proyectos.|  
  
### <a name="configuration-builder-object"></a>Objeto de generador de configuración  
  
|Interfaces|Comentarios|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|Administra la operación de compilación de una configuración del proyecto.|  
  
### <a name="additional-project-objects"></a>Objetos de proyecto adicionales  
  
|Interfaces|Comentarios|  
|----------------|--------------|  
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|Muestra elementos de propiedades en el **propiedades** ventana.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|Muestra las salidas para la implementación.|  
  
 En la tabla siguiente presenta breves descripciones de los servicios identificados en el modelo de proyecto.  
  
### <a name="services"></a>Servicios  
  
|web de Office|Comentarios|  
|-------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|Lo usan los VSPackages que implementan los tipos de proyecto para registrar que existe su generador de proyectos con el IDE. El VSPackage debe llamar a `QueryService` para este servicio y registre su generador de proyectos cuando `IVsPackage::SetSite` se llama al método. Si el `SetSite` no se llama al método, no se crea una instancia de su proyecto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Proporciona acceso a la noción interno, integrado del IDE de la solución actual, como la capacidad de enumerar los proyectos, crear nuevos proyectos, tenga en cuenta los cambios del proyecto y así sucesivamente.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|Lo llaman los proyectos que deseen participar en el control de código fuente.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|Mantiene una tabla de documentos abiertos para determinar si uno o varios de los elementos de proyecto ya están abiertos.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|Contiene las interfaces y métodos que se llama para abrir un elemento de proyecto mediante el editor estándar o un editor específico.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|Se requiere para ser llamado por todos los proyectos al que agregar, quitar o cambiar el nombre de sus elementos.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|Administra los cambios realizados en un archivo o directorio y notifica a los clientes cuando se han cambiado los archivos seleccionados en el disco.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|Se requiere para ser llamado por todos los proyectos y editores antes de integridad de los elementos o se guardan.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|Administra el orden de las operaciones de compilación e implementación de configuraciones de proyecto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|Proporciona acceso a servicios de depurador de bajo nivel que se usan para la mayoría de los controles de depuración.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|Habilita el acceso de los paquetes VSPackage para obtener información acerca de las selecciones actuales y permite la comunicación con el **propiedades** ventana.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Proporciona funcionalidad básica de IDE relacionadas con la interfaz de usuario, como la capacidad para crear y enumerar las ventanas de herramientas o ventanas de documento o para notificar un error al usuario.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|Proporciona acceso a la barra de estado del IDE.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|Se utiliza para implementar el modelo de automatización. En el modelo de proyecto, devolverá un objeto de propiedades que le permita crea una instancia de ese objeto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|Se utiliza para implementar eventos de Portapapeles en el objeto de proyecto en la jerarquía. `SVsUIHierWinClipboardHelper` le permite correctamente identificador operaciones de cortar, copiar y pegar.|  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Lista de comprobación: Creación de nuevos tipos de proyecto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [No está en la compilación: Uso de clases del proyecto de HierUtil7 para implementar un tipo de proyecto (C++)](http://msdn.microsoft.com/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [Herramientas de exploración de símbolos de compatibilidad](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Elementos de un modelo de proyecto](../../extensibility/internals/elements-of-a-project-model.md)
