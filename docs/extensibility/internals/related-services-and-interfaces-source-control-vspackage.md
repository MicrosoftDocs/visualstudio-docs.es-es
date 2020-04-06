---
title: Servicios e interfaces relacionados (VSPackage de control de código fuente) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, interfaces
- interfaces, source control packages
ms.assetid: 3e96e838-5675-46bb-99cf-40d420086038
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 533f1bf4fcfbaebb25ec10908abf4a46ddacd521
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705628"
---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>Interfaces y servicios relacionados (VSPackage de control de código fuente)
En esta sección se enumeran todas las interfaces relacionadas con VSPackage del control de código fuente en el [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]archivo . El control de código fuente VSPackage implementa algunas de estas interfaces y usa otras para realizar tareas de control de código fuente.

## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>Interfaces implementadas por y para VSPackages de Control de código fuente
 Las interfaces siguientes se [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]describen en el , y el control de código fuente VSPackage implementa un subconjunto de ellos en función de su conjunto de características deseado. Algunas interfaces se marcan como necesarias y deben implementarse en cada control de código fuente VSPackage.

 Para las interfaces que un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] paquete no implementa, proporciona una implementación predeterminada. Tenga en cuenta que la implementación predeterminada está diseñada para el caso cuando no se registra ningún VSPackage y no se controla ningún proyecto. Un control de código fuente correctamente escrito VSPackage implementa todas las interfaces necesarias en lugar de dejarlo en la implementación predeterminada de esas interfaces.

 Un control de código fuente VSPackage debe implementar un servicio privado que encapsula algunas o todas las interfaces siguientes.

 Las interfaces son:

- Requerido: la entidad adecuada (control de código fuente VSPackage, Código auxiliar de control de código fuente, proyecto) debe implementar la interfaz.

- Recomendado: La entidad debe implementar esta interfaz; de lo contrario, la funcionalidad de control de código fuente puede estar limitada.

- Opcional: la entidad puede implementar esta interfaz para proporcionar un conjunto de características más completo.

| Interfaz | Propósito | Implementado por | ¿Implementar? |
| - | - |--------------------------|-------------|
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> | Los editores llaman a esta interfaz antes de modificar o guardar un archivo. El control de código fuente VSPackage puede desproteger el archivo o denegar la operación si se produce un error en la desprotección. | Control de código fuente VSPackage | Recomendado |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> | Esta interfaz proporciona funcionalidad básica de control de código fuente para proyectos, como registrar y anular el registro de proyectos con control de código fuente y proporcionar compatibilidad con glifos de control de código fuente básicos. | Control de código fuente VSPackage | Obligatorio |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> | Esta interfaz se <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> obtiene <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> del uso de la función, o simplemente convirtiendo el objeto que se implementa `IVsHierarchy` en `IVsSccProject2`. Se utiliza para obtener los archivos bajo control de código fuente en un proyecto o para informar al proyecto del estado o la ubicación del control de código fuente actual. | proyecto | Obligatorio |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> | El módulo de integración utiliza esta interfaz para establecer el VSPackage activo actual. | Control de código fuente VSPackage | Obligatorio |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> | Esta interfaz se basa en un modelo de suscripción. Cualquier VSPackage puede indicar que desea recibir eventos de documento y ser advertido por el shell en los eventos que están a punto de suceder. Se implementa y controla [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]mediante , que a `IVsTrackProjectDocumentsEvents2` su vez pasa eventos que implementan el VSPackage. | Código de control de código fuente Stub | Obligatorio |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3> | Esta interfaz proporciona procesamiento por lotes, operaciones `OnQueryAddFiles` de lectura y escritura sincronizadas y un método avanzado. | Código de control de código fuente Stub | Obligatorio |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> | **El Explorador** de soluciones y los proyectos llaman a esta interfaz cuando se agregan nuevos archivos a los proyectos o cuando se cambia el nombre de los archivos y carpetas de los proyectos. El control de código fuente VSPackage puede desproteger el archivo de proyecto o cancelar la operación. | Control de código fuente VSPackage | Recomendado |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3> | **El Explorador** de soluciones y los proyectos llaman a esta interfaz en respuesta a las llamadas realizadas a los métodos de la IVstrackProjectDocuments3 interfaz. El control de código fuente VSPackage puede realizar un seguimiento de las `OnQueryAddFiles` operaciones por lotes, operaciones de lectura y escritura sincronizadas y trabajar con un método más avanzado. | Control de código fuente VSPackage | Recomendado |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation> | Esta interfaz proporciona compatibilidad con la administración de inscripción para proyectos web. | Control de código fuente VSPackage | Recomendado |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip> | Esta interfaz se utiliza para recuperar información sobre herramientas para los archivos controlados por código fuente en los proyectos. | Control de código fuente VSPackage | Opcional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl> | Esta interfaz proporciona compatibilidad con la extensión de espacio de nombres. | Control de código fuente VSPackage | Opcional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution> | El VSPackage usa esta interfaz para integrar una extensión de espacio de nombres en el **New**, **Open**o **Save** cuadros de diálogo. Por lo tanto, los proyectos se pueden agregar automáticamente al control de código fuente en la creación o agregar se al control de código fuente cuando una operación de guardado está en vigor. | Control de código fuente VSPackage | Opcional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs> | El VSPackage usa esta interfaz para definir glifos adicionales como glifos de control de código fuente para nodos en el **Explorador**de soluciones . | Control de código fuente VSPackage | Opcional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl> | El cuadro de diálogo **Agregar** para proyectos web utiliza esta interfaz. Proporciona métodos para buscar una ubicación de control de código fuente y para abrir un proyecto Web agregado previamente en el repositorio de control de código fuente en esa ubicación. | Control de código fuente VSPackage | Recomendado |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc> | Esta interfaz proporciona compatibilidad para la carga asincrónica (en segundo plano) de proyectos desde el control de código fuente. | Control de código fuente VSPackage | Opcional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents> | Esta interfaz permite a los proyectos ver <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>el progreso de la carga asincrónica iniciada por . | proyecto | Opcional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions> | Esta interfaz permite que el IDE para consultar el control de código fuente activo VSPackage. El IDE consulta el valor de la configuración del control de código fuente que tiene significado incluso cuando no hay ningún control de código fuente activo VSPackage registrado. Esta interfaz se implementa [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]y se controla mediante . | Código de control de código fuente Stub | Obligatorio |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> | Esta interfaz se utiliza para registrar el control de código fuente VSPackage. | Código de control de código fuente Stub | Obligatorio |
| <xref:EnvDTE.SourceControl> | Esta interfaz se utiliza en la automatización. Como tal, expone solo las funciones que se pueden ejecutar sin mostrar ninguna interfaz de usuario. | Control de código fuente VSPackage | Opcional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> | Esta interfaz se utiliza para guardar la configuración del control de código fuente en el archivo de solución (.sln). La configuración incluye la ubicación del control de código fuente y los indicadores de estado del control de código fuente. | Control de código fuente VSPackage | Recomendado |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> | Esta interfaz se utiliza para guardar la configuración del control de código fuente en el archivo de opciones de solución (.suo). Esto puede incluir la configuración de control de código fuente específica del usuario, como la ubicación de inscripción del usuario actual. | Control de código fuente VSPackage | Recomendado |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> | Esta interfaz se utiliza para supervisar eventos con el fin de realizar operaciones como la comprobación de archivos de proyecto antes de cerrar soluciones o obtener nuevos archivos del control de código fuente al abrir un proyecto. | Control de código fuente VSPackage | Recomendado |

## <a name="see-also"></a>Vea también
- [Elementos de diseño](../../extensibility/internals/source-control-vspackage-design-elements.md)
