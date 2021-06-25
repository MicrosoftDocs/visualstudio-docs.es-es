---
title: Componentes principales del modelo de proyecto | Microsoft Docs
description: Este artículo contiene descripciones de las interfaces y servicios identificados en el núcleo del modelo de proyecto y las interfaces y servicios asociados a los objetos .
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- project models, objects and interfaces
- project models, services
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 88dc53378e7e06d0a7d4ad362f7bb3876e186c80
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899711"
---
# <a name="project-model-core-components"></a>Componentes principales del modelo de proyecto
Las tablas siguientes se expanden en el modelo de proyecto. Las tablas presentan breves descripciones de las interfaces y servicios identificados en el modelo, así como las interfaces y servicios asociados a objetos específicos. Además, las tablas detallan otras interfaces que son opcionales en la creación y el mantenimiento del proyecto en función de los requisitos del tipo de proyecto específico.

 Para obtener más información, [vea Supporting Symbol-Browsing Tools](../../extensibility/internals/supporting-symbol-browsing-tools.md).

### <a name="package-object"></a>Objeto package

|Interfaz|Comentarios|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|Inicializa un VSPackage en el IDE y pone sus servicios a disposición del IDE.|

### <a name="project-factory-object"></a>Objeto de Generador de proyectos

|Interfaz|Comentarios|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|Administra la creación de nuevos proyectos y la apertura de proyectos existentes.|

### <a name="project-objects"></a>Objetos de proyecto

|Interfaces|Comentarios|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|Administra la adición y eliminación de elementos de proyecto, abre editores y mantiene la asignación entre cada moniker de documento y `VSITEMID` . Hereda de `IVsProject` y `IVsProject2` .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|Administra las propiedades de navegación y visualización y proporciona eventos.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|Habilita la ejecución de comandos similar a la de para comandos como Cortar y Cambiar nombre que solo se aplican cuando el foco está `IOleCommandTarget` en Explorador de soluciones.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Actúa como la interfaz de destino del comando principal para una jerarquía de proyectos. Es la interfaz estándar para consultar los objetos de su estado o estado de comando y ejecutar comandos. Disponible cuando no está centrado en la ventana Proyecto.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Coordina la persistencia del estado del proyecto. Normalmente, el estado del proyecto se almacena como un archivo de proyecto, pero se puede adaptar a sistemas de almacenamiento que no están basados en archivos.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|Permite al proyecto administrar todos los aspectos de persistencia de sus elementos de proyecto, ya sea como archivos en disco u objetos en otros sistemas de almacenamiento. La `IVsPersistHierarchyItem2` interfaz se usa para los elementos que no implementan la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Coordina las interacciones con el control de código fuente.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|Permite a los proyectos administrar la información de configuración.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|Administra los objetos de configuración del proyecto, como las configuraciones debug/release. Las operaciones de compilación, implementación y depuración se coordinan a través de objetos de configuración del proyecto.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|Implementado por jerarquías para controlar las opciones de eliminación (destructiva) o eliminación (no destructiva) de los elementos de jerarquía. Llame a la interfaz de consulta `IVsHierarchyDeleteHandler` en la interfaz desde la interfaz `IVsHierarchy` .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|Proporciona la opción de implementación de tener el objeto que admite la interfaz en una identidad COM diferente a la del objeto `IVsCfgProvider2` de proyecto que implementa la interfaz `IVsHierarchy` .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|Interfaz opcional implementada para que otros desarrolladores puedan ampliar el proyecto. La interfaz permite a un VSPackage de terceros registrar un GUID que se conserva en el archivo de proyecto para que cada vez que se carga el proyecto, cargue el GUID de servicio de terceros en el archivo del proyecto y llame a para ese `IVsProjectStartupServices` `QueryService` GUID.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|Implementado por jerarquías de origen en una ventana para coordinar operaciones del `UIHierarchy` Portapapeles como cortar, copiar y pegar. Use la interfaz `AdviseClipboardHelperEvents` para registrar eventos del Portapapeles.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|Proporciona información sobre un elemento arrastrado con respecto a su origen de datos durante una operación de arrastrar y colocar en una ventana de jerarquía de interfaz de usuario. Se llama desde la `IVsHierarchy` interfaz .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|Proporciona información sobre un elemento arrastrado con respecto a su destino de colocación durante una operación de arrastrar y colocar en una ventana de jerarquía de interfaz de usuario. Se llama desde la `IVsHierarchy` interfaz .|

### <a name="configuration-object"></a>objeto de configuración

|Interfaces|Comentarios|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|Proporciona información sobre una configuración.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|Permite a los proyectos administrar la información de configuración.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|Permite ejecutar un proyecto bajo el control del depurador.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|Implementado por proyectos de implementación que realizan operaciones de implementación para otros proyectos.|

### <a name="configuration-builder-object"></a>Objeto de Generador de configuración

|Interfaces|Comentarios|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|Administra la operación de compilación de una configuración del proyecto.|

### <a name="additional-project-objects"></a>Objetos de proyecto adicionales

|Interfaces|Comentarios|
|----------------|--------------|
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|Muestra las propiedades del elemento en la **ventana** Propiedades.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|Muestra las salidas para la implementación.|

 En la tabla siguiente se presentan breves descripciones de los servicios identificados en el modelo de proyecto.

### <a name="services"></a>Servicios

|Servicio|Comentarios|
|-------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|Usado por vspackages que implementan tipos de proyecto para registrar que su generador de proyectos existe con el IDE. El VSPackage debe llamar `QueryService` a para este servicio y registrar su generador de proyectos cuando se llama al método `IVsPackage::SetSite` . Si no se llama al método , no se crea una instancia `SetSite` del proyecto.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Proporciona acceso a la noción interna integrada del IDE de la solución actual, como la capacidad de enumerar proyectos, crear nuevos proyectos, tomar nota de los cambios del proyecto, y así sucesivamente.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|Lo llaman los proyectos que desean participar en el control de código fuente.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|Mantiene una tabla de documentos abiertos para determinar si uno o varios de los elementos del proyecto ya están abiertos.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|Contiene las interfaces y métodos a los que se llama para abrir realmente un elemento de proyecto mediante el editor estándar o un editor específico.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|Todos los proyectos deben llamarlos cuando agreguen, quiten o cambien el nombre de sus elementos.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|Administra los cambios en un archivo o directorio y notifica a los clientes cuándo se han cambiado los archivos seleccionados en el disco.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|Es necesario que todos los proyectos y editores los llamen antes de desasuciar elementos o guardarlos.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|Administra el orden de las operaciones de compilación e implementación para las configuraciones del proyecto.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|Proporciona acceso a los servicios del depurador de bajo nivel que se usan para la mayoría de los controles de depuración.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|Habilita el acceso de VSPackages a información sobre las selecciones actuales y permite la comunicación con la **ventana** Propiedades.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Proporciona funcionalidad básica del IDE relacionada con la interfaz de usuario, como la capacidad de crear y enumerar ventanas de herramientas o ventanas de documentos, o para notificar un error al usuario.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|Proporciona acceso a la barra de estado del IDE.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|Se usa para implementar el modelo de automatización. En el modelo de proyecto, devolverá un objeto properties que le permite crear una instancia de ese objeto.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|Se usa para implementar eventos del Portapapeles en el objeto de proyecto en la jerarquía. `SVsUIHierWinClipboardHelper` permite controlar correctamente las operaciones de cortar, copiar y pegar.|

## <a name="see-also"></a>Consulta también
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Lista de comprobación: Creación de nuevos tipos de proyectos](../../extensibility/internals/checklist-creating-new-project-types.md)
- [No está en la compilación: usar clases de proyecto HierUtil7 para implementar un tipo de proyecto (C++)](/previous-versions/bb166212(v=vs.100))
- [Compatibilidad con herramientas de exploración de símbolos](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Elementos de un modelo de proyecto](../../extensibility/internals/elements-of-a-project-model.md)