---
title: Interfaces y servicios relacionados (VSPackage de control de código fuente)
titleSuffix: ''
description: Obtenga información sobre las interfaces relacionadas con VSPackage del control de código fuente en Visual Studio SDK. El paquete implementa algunas interfaces y usa otras para el control de código fuente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- source control packages, interfaces
- interfaces, source control packages
ms.assetid: 3e96e838-5675-46bb-99cf-40d420086038
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6385307c91541204d58228b489160888f79dec85
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903338"
---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>Interfaces y servicios relacionados (VSPackage de control de código fuente)

En esta sección se enumeran todas las interfaces relacionadas con VSPackage del control de código fuente en [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] . El VSPackage de control de código fuente implementa algunas de estas interfaces y usa otras para realizar tareas de control de código fuente.

## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>Interfaces implementadas por y para VSPackages de control de código fuente

 Las interfaces siguientes se describen en y el control de código fuente VSPackage implementa un subconjunto de ellas en función de [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] su conjunto de características deseado. Algunas interfaces se marcan como necesarias y deben implementarse mediante cada VSPackage de control de código fuente.

 Para las interfaces que un paquete no implementa, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proporciona una implementación predeterminada. Tenga en cuenta que la implementación predeterminada está diseñada para el caso en que no se registra ningún VSPackage y no se controla ningún proyecto. Un VSPackage de control de código fuente escrito correctamente implementa todas las interfaces necesarias en lugar de dejarla en la implementación predeterminada de esas interfaces.

 Un VSPackage de control de código fuente debe implementar un servicio privado que encapsula algunas o todas las interfaces siguientes.

 Las interfaces son:

- Requerido: la entidad adecuada (VSPackage de control de código fuente, código auxiliar de control de código fuente, proyecto) debe implementar la interfaz .

- Recomendado: la entidad debe implementar esta interfaz; De lo contrario, la funcionalidad del control de código fuente puede estar limitada.

- Opcional: la entidad puede implementar esta interfaz para proporcionar un conjunto de características más completo.

| Interfaz | Propósito | Implementado por | ¿Implementar? |
| - | - |--------------------------|-------------|
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> | Los editores llaman a esta interfaz antes de modificar o guardar un archivo. El VSPackage del control de código fuente puede desprotegir el archivo o denegar la operación si se produce un error en la desprotección. | VSPackage de control de código fuente | Recomendado |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> | Esta interfaz proporciona funcionalidad básica de control de código fuente para proyectos, como registrar y anular el registro de proyectos con control de código fuente y proporcionar compatibilidad con glifos de control de código fuente básicos. | VSPackage de control de código fuente | Obligatorio |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> | Esta interfaz se obtiene de mediante la función o simplemente al convertir <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> el objeto que se implementa en <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> `IVsHierarchy` `IVsSccProject2` . Se usa para obtener los archivos bajo control de código fuente en un proyecto o para informar al proyecto del estado o la ubicación del control de código fuente actual. | Project | Obligatorio |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> | El módulo de integración usa esta interfaz para establecer el VSPackage activo actual. | VSPackage de control de código fuente | Obligatorio |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> | Esta interfaz se basa en un modelo de suscripción. Cualquier VSPackage puede indicar que desea recibir eventos de documento y que el shell le aconseja sobre los eventos que están a punto de ocurrir. Se implementa y controla mediante , que a su vez pasa eventos [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que implementan `IVsTrackProjectDocumentsEvents2` al VSPackage. | Código auxiliar del control de código fuente | Obligatorio |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3> | Esta interfaz proporciona procesamiento por lotes, operaciones de lectura y escritura sincronizadas y un método `OnQueryAddFiles` avanzado. | Código auxiliar del control de código fuente | Obligatorio |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> | **Explorador de soluciones** y los proyectos llaman a esta interfaz cuando se agregan nuevos archivos a los proyectos o cuando se cambia el nombre de los archivos y carpetas o se eliminan de los proyectos. El VSPackage del control de código fuente puede desenlazar el archivo del proyecto o cancelar la operación. | VSPackage de control de código fuente | Recomendado |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3> | **Explorador de soluciones** y los proyectos llaman a esta interfaz en respuesta a las llamadas realizadas a los métodos de la interfaz IVstrackProjectDocuments3. El VSPackage de control de código fuente puede realizar un seguimiento de las operaciones por lotes, las operaciones de lectura y escritura sincronizadas y trabajar con un método más `OnQueryAddFiles` avanzado. | VSPackage de control de código fuente | Recomendado |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation> | Esta interfaz proporciona compatibilidad con la administración de la alta para proyectos web. | VSPackage de control de código fuente | Recomendado |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip> | Esta interfaz se usa para recuperar información sobre herramientas para los archivos controlados por código fuente en los proyectos. | VSPackage de control de código fuente | Opcionales |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl> | Esta interfaz proporciona compatibilidad con la extensión de espacio de nombres. | VSPackage de control de código fuente | Opcionales |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution> | El VSPackage usa esta interfaz para integrar una extensión de espacio de nombres en los **cuadros** de diálogo **Nuevo,** Abrir **o** Guardar. Por lo tanto, los proyectos se pueden agregar automáticamente al control de código fuente al crearse o agregarse al control de código fuente cuando una operación de guardado está en vigor. | VSPackage de control de código fuente | Opcionales |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs> | EL VSPackage usa esta interfaz para definir glifos adicionales como glifos de control de código fuente para los nodos **de Explorador de soluciones**. | VSPackage de control de código fuente | Opcionales |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl> | El **cuadro de** diálogo Agregar para proyectos web usa esta interfaz. Proporciona métodos para examinar una ubicación de control de código fuente y para abrir un proyecto web agregado anteriormente en el repositorio de control de código fuente en esa ubicación. | VSPackage de control de código fuente | Recomendado |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc> | Esta interfaz proporciona compatibilidad para la carga asincrónica (en segundo plano) de proyectos desde el control de código fuente. | VSPackage de control de código fuente | Opcionales |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents> | Esta interfaz permite a los proyectos ver el progreso de la carga asincrónica iniciada por <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc> . | Project | Opcionales |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions> | Esta interfaz permite al IDE consultar el VSPackage del control de código fuente activo. El IDE consulta el valor de la configuración del control de código fuente que tiene significado incluso cuando no hay ningún VSPackage de control de código fuente activo registrado. Esta interfaz se implementa y controla mediante [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . | Código auxiliar del control de código fuente | Obligatorio |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> | Esta interfaz se usa para registrar el vsPackage del control de código fuente. | Código auxiliar del control de código fuente | Obligatorio |
| <xref:EnvDTE.SourceControl> | Esta interfaz se usa en la automatización. Por lo tanto, solo expone funciones que se pueden ejecutar sin mostrar ninguna interfaz de usuario. | VSPackage de control de código fuente | Opcionales |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> | Esta interfaz se usa para guardar la configuración del control de código fuente en el archivo de solución (.sln). La configuración incluye la ubicación del control de código fuente y las marcas de estado del control de código fuente. | VSPackage de control de código fuente | Recomendado |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> | Esta interfaz se usa para guardar la configuración del control de código fuente en el archivo de opciones de solución (.suo). Esto puede incluir la configuración de control de código fuente específica del usuario, como la ubicación de registro del usuario actual. | VSPackage de control de código fuente | Recomendado |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> | Esta interfaz se usa para supervisar eventos con el fin de realizar operaciones como la comprobación de archivos de proyecto antes de cerrar soluciones o la obtención de nuevos archivos del control de código fuente al abrir un proyecto. | VSPackage de control de código fuente | Recomendado |

## <a name="see-also"></a>Consulta también
- [Elementos de diseño](../../extensibility/internals/source-control-vspackage-design-elements.md)
