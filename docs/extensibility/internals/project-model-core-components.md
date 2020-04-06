---
title: Componentes del núcleo del modelo de proyecto (Project Model Core Components) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project models, objects and interfaces
- project models, services
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34f65973f0f3edc1dd6264c32d165503dca78681
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706537"
---
# <a name="project-model-core-components"></a>Componentes principales del modelo de proyecto
Las tablas siguientes se expanden en el modelo de proyecto. Las tablas presentan breves descripciones de las interfaces y servicios identificados en el modelo, y las interfaces y servicios asociados con objetos específicos. Además, las tablas detallan otras interfaces que son opcionales en la creación y el mantenimiento del proyecto en función de los requisitos de su tipo de proyecto específico.

 Para obtener más información, consulte Compatibilidad con herramientas [de exploración de símbolos](../../extensibility/internals/supporting-symbol-browsing-tools.md).

### <a name="package-object"></a>Objeto de paquete

|Interfaz|Comentarios|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|Inicializa un VSPackage en el IDE y hace que sus servicios estén disponibles para el IDE.|

### <a name="project-factory-object"></a>Objeto Project Factory

|Interfaz|Comentarios|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|Gestiona la creación de nuevos proyectos y la apertura de proyectos existentes.|

### <a name="project-objects"></a>Objetos de proyecto

|Interfaces|Comentarios|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|Administra la adición y eliminación de elementos de proyecto, abre `VSITEMID`editores y mantiene la asignación entre cada moniker de documento y el archivo . Hereda `IVsProject` de `IVsProject2`y .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|Administra las propiedades de navegación y visualización y proporciona eventos.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|Habilita la ejecución de `IOleCommandTarget` comandos similar a la de los comandos como Cortar y Cambiar nombre que se aplican solo cuando el foco está en el Explorador de soluciones.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Sirve como interfaz de destino de comando principal para una jerarquía de proyectos. Es la interfaz estándar para consultar objetos para su estado de comando o estado y ejecutar comandos. Disponible cuando no está enfocado en la ventana Proyecto.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Coordina la persistencia del estado del proyecto. Normalmente, el estado del proyecto se almacena como un archivo de proyecto, pero se puede adaptar a sistemas de almacenamiento que no están basados en archivos.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|Permite al proyecto administrar todos los aspectos de la persistencia de los elementos de proyecto, ya sea como archivos en disco u objetos en otros sistemas de almacenamiento. La `IVsPersistHierarchyItem2` interfaz se utiliza para <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> los elementos que no implementan la interfaz.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Coordina las interacciones con el control de código fuente.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|Permite que los proyectos administren la información de configuración.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|Administra objetos de configuración de proyecto, como configuraciones de depuración/liberación. Las operaciones de compilación, implementación y depuración se coordinan a través de objetos de configuración de proyecto.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|Implementado por jerarquías para controlar las opciones de eliminación (destructiva) o eliminación (no destructivas) para los elementos de jerarquía. Interfaz de `IVsHierarchyDeleteHandler` consulta de `IVsHierarchy` llamada en la interfaz de la interfaz.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|Proporciona la opción de implementación `IVsCfgProvider2` de tener el objeto que admite la `IVsHierarchy` interfaz en una identidad COM diferente que el objeto de proyecto que implementa la interfaz.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|Interfaz opcional implementada para que el proyecto sea extensible por otros desarrolladores. La `IVsProjectStartupServices` interfaz permite que un VSPackage de terceros registre un GUID que se conserva en el archivo de proyecto para `QueryService` que cada vez que se carga el proyecto, cargue el GUID del servicio de terceros en el archivo de proyecto y llame a ese GUID.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|Se implementa mediante jerarquías `UIHierarchy` de origen en una ventana para coordinar operaciones del portapapeles como cortar, copiar y pegar. Utilice `AdviseClipboardHelperEvents` la interfaz para registrar eventos del portapapeles.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|Proporciona información sobre un elemento arrastrado en relación con su origen de datos durante una operación de arrastrar y colocar en una ventana de jerarquía de interfaz de usuario. Se llama `IVsHierarchy` desde la interfaz.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|Proporciona información sobre un elemento arrastrado en relación con su destino de colocación durante una operación de arrastrar y colocar en una ventana de jerarquía de interfaz de usuario. Se llama `IVsHierarchy` desde la interfaz.|

### <a name="configuration-object"></a>objeto de configuración

|Interfaces|Comentarios|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|Proporciona información sobre una configuración.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|Permite que los proyectos administren la información de configuración.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|Permite ejecutar un proyecto bajo el control del depurador.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|Implementado por proyectos de implementación que realizan operaciones de implementación para otros proyectos.|

### <a name="configuration-builder-object"></a>Objeto Configuration Builder

|Interfaces|Comentarios|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|Administra la operación de compilación de una configuración del proyecto.|

### <a name="additional-project-objects"></a>Objetos adicionales del proyecto

|Interfaces|Comentarios|
|----------------|--------------|
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|Muestra las propiedades del elemento en la ventana **Propiedades.**|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|Muestra las salidas para la implementación.|

 En la tabla siguiente se presentan breves descripciones de los servicios identificados en el modelo de proyecto.

### <a name="services"></a>Servicios

|Servicio|Comentarios|
|-------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|Utilizado por VSPackages que implementan tipos de proyecto para registrar que su generador de proyectos existe con el IDE. El VSPackage `QueryService` debe llamar a este servicio `IVsPackage::SetSite` y registrar su generador de proyectos cuando se llama al método. Si `SetSite` no se llama al método, no se crea una instancia del proyecto.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Proporciona acceso a la noción interna integrada del IDE de la solución actual, como la capacidad de enumerar proyectos, crear nuevos proyectos, tomar nota de los cambios del proyecto, etc.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|Llamado por proyectos que desean participar en el control de código fuente.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|Mantiene una tabla de documentos abiertos para determinar si uno o varios de los elementos del proyecto ya están abiertos.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|Contiene las interfaces y métodos a los que se llama para abrir realmente un elemento de proyecto mediante el editor estándar o un editor específico.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|Todos los proyectos deben llamarlos cuando agregan, quitan o cambian el nombre de sus elementos.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|Administra los cambios en un archivo o directorio y notifica a los clientes cuando se han cambiado los archivos seleccionados en el disco.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|Se requiere que todos los proyectos y editores sean llamados antes de que ensucien los elementos o los guarden.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|Administra el orden de las operaciones de compilación e implementación para las configuraciones de proyecto.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|Proporciona acceso a los servicios de depurador de bajo nivel utilizados para la mayoría de los controles de depuración.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|Habilita VSPackages acceso a información sobre las selecciones actuales y habilita la comunicación con el **propiedades** ventana.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Proporciona funcionalidad básica de IDE relacionada con la interfaz de usuario, como la capacidad de crear y enumerar ventanas de herramientas o ventanas de documentos o para notificar un error al usuario.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|Proporciona acceso a la barra de estado del IDE.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|Se utiliza para implementar el modelo de automatización. En el modelo de proyecto, devolverá un objeto properties que le permite crear una instancia de ese objeto.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|Se utiliza para implementar eventos de portapapeles en el objeto de proyecto en la jerarquía. `SVsUIHierWinClipboardHelper`le permite manejar correctamente las operaciones de cortar, copiar y pegar.|

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Lista de comprobación: creación de nuevos tipos de proyecto](../../extensibility/internals/checklist-creating-new-project-types.md)
- [No en compilación: uso de clases de proyecto HierUtil7 para implementar un tipo de proyecto (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)
- [Compatibilidad con herramientas de exploración de símbolos](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Elementos de un modelo de proyecto](../../extensibility/internals/elements-of-a-project-model.md)
