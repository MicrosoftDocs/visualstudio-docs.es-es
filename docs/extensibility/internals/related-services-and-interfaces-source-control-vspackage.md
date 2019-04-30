---
title: Interfaces (VSPackage de Control de código fuente) y servicios relacionados | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, interfaces
- interfaces, source control packages
ms.assetid: 3e96e838-5675-46bb-99cf-40d420086038
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a792bc7b0c64b7e509e6d426c8b4f33c9f816276
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62908558"
---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>Interfaces y servicios relacionados (VSPackage de control de código fuente)
Esta sección enumeran todas las interfaces de VSPackage de control de origen al [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]. El control de código fuente VSPackage implementa algunas de estas interfaces y utiliza otros usuarios para realizar tareas de control de código fuente.

## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>Interfaces implementadas por y para VSPackages de Control de código fuente
 Las interfaces siguientes se describen en la [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], y el control de código fuente VSPackage implementa un subconjunto de ellas, dependiendo de su conjunto de características deseadas. Algunas de las interfaces se marcan como requerido y debe ser implementada por cada VSPackage de control de código fuente.

 Para las interfaces que implementa un paquete, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proporciona una implementación predeterminada. Tenga en cuenta que la implementación predeterminada está diseñada para el caso cuando no se registra ningún paquete de VS y no se controla ningún proyecto. Un control de código fuente escrito correctamente VSPackage implementa interfaces toda en lugar de dejarlo para la implementación predeterminada de esas interfaces.

 Un VSPackage de control de origen debe implementar un servicio privado que encapsula algunas o todas las interfaces siguientes.

 Las interfaces son:

- Obligatorio: La entidad adecuada (control de código fuente VSPackage, código auxiliar de Control de código fuente, project) debe implementar la interfaz.

- Recomendado: La entidad debe implementar esta interfaz; en caso contrario, la funcionalidad de control de código fuente puede ser limitada.

- Opcional: la entidad puede implementar esta interfaz para proporcionar un conjunto de características más completo.

| Interfaz | Finalidad | Implementado por | ¿Implementar? |
| - | - |--------------------------|-------------|
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> | Editores de llamar a esta interfaz antes de modificar o guardar un archivo. El control de código fuente VSPackage puede desproteger el archivo o denegar la operación si se produce un error en la desprotección. | VSPackage de control de código fuente | Se recomienda |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> | Esta interfaz proporciona funcionalidad de control de código fuente básicos para los proyectos, como registrar y anular el registro de los proyectos con control de código fuente y proporcionar soporte técnico para los glifos de control de código fuente básicos. | VSPackage de control de código fuente | Obligatorio |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> | Esta interfaz se obtiene desde el <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> utilizando el <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> función, o simplemente convirtiendo el objeto que implementa `IVsHierarchy` a `IVsSccProject2`. Se usa para obtener los archivos bajo control de código fuente en un proyecto o para informar el proyecto de la ubicación o estado de control de código fuente actual. | Proyecto | Obligatorio |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> | El módulo de integración usa esta interfaz para establecer el VSPackage activo actual. | VSPackage de control de código fuente | Obligatorio |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> | Esta interfaz se basa en un modelo de suscripción. Cualquier VSPackage puede indicar que desea recibir eventos de documento y tenga en cuenta el shell de eventos que están a punto de suceder. Se implementa y administra [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], que a su vez pasa los eventos que implementa el `IVsTrackProjectDocumentsEvents2` al VSPackage. | Código auxiliar de Control de código fuente | Obligatorio |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3> | Esta interfaz proporciona el procesamiento por lotes, las operaciones de lectura/escritura sincronizados y un avanzado `OnQueryAddFiles` método. | Código auxiliar de Control de código fuente | Obligatorio |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> | **El Explorador de soluciones** y proyectos de llamar a esta interfaz cuando se agregan nuevos archivos a los proyectos, o cuando se cambia el nombre o se elimina de proyectos de archivos y carpetas. El control de código fuente VSPackage puede desproteger el archivo de proyecto o cancelar la operación. | VSPackage de control de código fuente | Se recomienda |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3> | **El Explorador de soluciones** y proyectos de llamar a esta interfaz en respuesta a las llamadas realizadas a los métodos de la interfaz IVstrackProjectDocuments3. El control de código fuente VSPackage puede realizar un seguimiento de las operaciones por lotes, sincronizadas las operaciones de lectura/escritura y trabajar con más avanzados `OnQueryAddFiles` método. | VSPackage de control de código fuente | Se recomienda |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation> | Esta interfaz proporciona compatibilidad con la administración de inscripción para los proyectos Web. | VSPackage de control de código fuente | Se recomienda |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip> | Esta interfaz se usa para recuperar información sobre herramientas para los archivos controlados por código fuente en los proyectos. | VSPackage de control de código fuente | Optional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl> | Esta interfaz proporciona compatibilidad con extensiones de espacio de nombres. | VSPackage de control de código fuente | Optional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution> | El paquete VSPackage usa esta interfaz para integrar una extensión de espacio de nombres en el **New**, **abierto**, o **guardar** cuadros de diálogo. Por lo tanto, los proyectos pueden automáticamente agrega al control de código fuente durante la creación, o agregar a control de código fuente cuando una operación de guardar operación está en vigor. | VSPackage de control de código fuente | Optional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs> | El paquete VSPackage usa esta interfaz se definen los glifos adicionales como glifos de control de código fuente para los nodos en **el Explorador de soluciones**. | VSPackage de control de código fuente | Optional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl> | El **agregar** cuadro de diálogo para proyectos Web usa esta interfaz. Proporciona métodos para examinar una ubicación de control de código fuente y para abrir un proyecto Web que agregó anteriormente en el repositorio de control de origen en esa ubicación. | VSPackage de control de código fuente | Se recomienda |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc> | Esta interfaz proporciona compatibilidad para la carga asincrónica (en segundo plano) de proyectos de control de código fuente. | VSPackage de control de código fuente | Optional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents> | Esta interfaz permite a los proyectos ver el progreso de la carga asincrónica iniciada por <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>. | Proyecto | Optional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions> | Esta interfaz permite que el IDE consultar el VSPackage de control de origen activo. El IDE consulta el valor de configuración de control de código fuente que tienen un significado, incluso cuando no hay ningún control de origen activo que VSPackage registrado. Esta interfaz se implementa y administra [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. | Código auxiliar de Control de código fuente | Obligatorio |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> | Esta interfaz se usa para registrar el VSPackage de control de código fuente. | Código auxiliar de Control de código fuente | Obligatorio |
| <xref:EnvDTE.SourceControl> | Esta interfaz se usa en la automatización. Por lo tanto, expone solo las funciones que se pueden ejecutar sin mostrar ninguna interfaz de usuario. | VSPackage de control de código fuente | Optional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> | Esta interfaz se utiliza para guardar el origen de configuración del control en el archivo de solución (.sln). La configuración incluye la ubicación del control de código fuente y las marcas de estado de control de código fuente. | VSPackage de control de código fuente | Se recomienda |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> | Esta interfaz se utiliza para guardar la configuración de control de código fuente en el archivo de solución (.suo) de opciones. Esto puede incluir la configuración de control de origen específicas para el usuario como la ubicación de la inscripción del usuario actual. | VSPackage de control de código fuente | Se recomienda |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> | Esta interfaz se utiliza para supervisar los eventos con el fin de realizar operaciones como la comprobación en los archivos de proyecto antes de cerrar soluciones o la obtención de los nuevos archivos de control de código fuente al abrir un proyecto. | VSPackage de control de código fuente | Se recomienda |

## <a name="see-also"></a>Vea también
- [Elementos de diseño](../../extensibility/internals/source-control-vspackage-design-elements.md)