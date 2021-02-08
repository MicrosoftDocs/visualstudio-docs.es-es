---
title: Interfaces y servicios relacionados (VSPackage de control de código fuente)
titleSuffix: ''
description: Obtenga información sobre las interfaces relacionadas con VSPackage de control de código fuente en el SDK de Visual Studio. El paquete implementa algunas interfaces y utiliza otras para el control de código fuente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, interfaces
- interfaces, source control packages
ms.assetid: 3e96e838-5675-46bb-99cf-40d420086038
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3cb7811816c4ad7a7ca6f6f0220f185799ee8b77
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837195"
---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>Interfaces y servicios relacionados (VSPackage de control de código fuente)

En esta sección se enumeran todas las interfaces relacionadas con VSPackage de control de código fuente en [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] . El VSPackage de control de código fuente implementa algunas de estas interfaces y utiliza otras para realizar las tareas de control de código fuente.

## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>Interfaces implementadas por y para VSPackages de control de código fuente

 Las siguientes interfaces se describen en [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] , y el VSPackage de control de código fuente implementa un subconjunto de ellas en función del conjunto de características deseado. Algunas interfaces se marcan como necesarias y deben implementarse en cada VSPackage de control de código fuente.

 Para las interfaces que un paquete no implementa, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proporciona una implementación predeterminada. Tenga en cuenta que la implementación predeterminada está diseñada para el caso de que no se registre ningún VSPackage y no se controle ningún proyecto. Un VSPackage de control de código fuente escrito correctamente implementa todas las interfaces necesarias en lugar de mantenerla en la implementación predeterminada de esas interfaces.

 Un VSPackage de control de código fuente debe implementar un servicio privado que encapsule algunas o todas las interfaces siguientes.

 Las interfaces son:

- Requerido: la entidad adecuada (VSPackage de control de código fuente, código auxiliar de control de código fuente y proyecto) debe implementar la interfaz.

- Recomendado: la entidad debe implementar esta interfaz; de lo contrario, la funcionalidad de control de código fuente puede estar limitada.

- Opcional: la entidad puede implementar esta interfaz para proporcionar un conjunto de características más completo.

| Interfaz | Propósito | Implementado por | Ejecutar? |
| - | - |--------------------------|-------------|
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> | Los editores llaman a esta interfaz antes de modificar o guardar un archivo. El VSPackage de control de código fuente puede desproteger el archivo o denegar la operación si se produce un error en la desprotección. | VSPackage de control de código fuente | Recomendado |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> | Esta interfaz proporciona funcionalidad básica de control de código fuente para los proyectos, como registrar y anular el registro de proyectos con el control de código fuente y proporcionar compatibilidad con los glifos básicos de control de código fuente. | VSPackage de control de código fuente | Obligatorio |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> | Esta interfaz se obtiene de <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> mediante la <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> función, o simplemente convirtiendo el objeto que implementa `IVsHierarchy` en `IVsSccProject2` . Se utiliza para obtener los archivos bajo control de código fuente en un proyecto o para informar del proyecto de la ubicación o el estado del control de código fuente actual. | Project | Obligatorio |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> | El módulo de integración utiliza esta interfaz para establecer el VSPackage activo actual. | VSPackage de control de código fuente | Obligatorio |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> | Esta interfaz se basa en un modelo de suscripción. Cualquier VSPackage puede indicar que desea recibir eventos de documento y que el shell le aconseje los eventos que están a punto de producirse. Lo implementa y controla [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , que a su vez pasa los eventos que implementan `IVsTrackProjectDocumentsEvents2` en el VSPackage. | Código auxiliar de control de código fuente | Obligatorio |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3> | Esta interfaz proporciona el procesamiento por lotes, las operaciones de lectura y escritura sincronizadas y un `OnQueryAddFiles` método avanzado. | Código auxiliar de control de código fuente | Obligatorio |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> | Los proyectos de **Explorador de soluciones** y llaman a esta interfaz cuando se agregan nuevos archivos a los proyectos, o cuando se cambia el nombre de los archivos y las carpetas de los proyectos. El VSPackage de control de código fuente puede desproteger el archivo de proyecto o cancelar la operación. | VSPackage de control de código fuente | Recomendado |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3> | **Explorador de soluciones** y proyectos llaman a esta interfaz en respuesta a las llamadas realizadas a los métodos de la interfaz IVstrackProjectDocuments3. El VSPackage de control de código fuente puede realizar un seguimiento de las operaciones por lotes, las operaciones de lectura/escritura sincronizadas y el trabajo con un método más avanzado `OnQueryAddFiles` . | VSPackage de control de código fuente | Recomendado |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation> | Esta interfaz proporciona compatibilidad con la administración de alta para proyectos Web. | VSPackage de control de código fuente | Recomendado |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip> | Esta interfaz se utiliza para recuperar la información sobre herramientas para los archivos controlados por código fuente en los proyectos de. | VSPackage de control de código fuente | Opcional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl> | Esta interfaz proporciona compatibilidad con la extensión de espacio de nombres. | VSPackage de control de código fuente | Opcional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution> | El VSPackage usa esta interfaz para integrar una extensión de espacio de nombres en los cuadros de diálogo **nuevos**, **abrir** o **Guardar** . Por consiguiente, los proyectos se pueden agregar automáticamente al control de código fuente al crearlos o agregarlos al control de código fuente cuando una operación de guardar está en vigor. | VSPackage de control de código fuente | Opcional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs> | El VSPackage usa esta interfaz para definir glifos adicionales como glifos de control de código fuente para los nodos de **Explorador de soluciones**. | VSPackage de control de código fuente | Opcional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl> | El cuadro de diálogo **Agregar** para proyectos web utiliza esta interfaz. Proporciona métodos para buscar una ubicación de control de código fuente y abrir un proyecto web agregado anteriormente en el repositorio de control de código fuente en esa ubicación. | VSPackage de control de código fuente | Recomendado |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc> | Esta interfaz proporciona compatibilidad para la carga asincrónica (en segundo plano) de proyectos desde el control de código fuente. | VSPackage de control de código fuente | Opcional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents> | Esta interfaz permite a los proyectos ver el progreso de la carga asincrónica iniciada por <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc> . | Project | Opcional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions> | Esta interfaz permite al IDE consultar el VSPackage de control de código fuente activo. El IDE consulta el valor de la configuración de control de código fuente que tiene un significado incluso cuando no hay registrado ningún VSPackage de control de código fuente activo. Esta interfaz la implementa y controla [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . | Código auxiliar de control de código fuente | Obligatorio |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> | Esta interfaz se usa para registrar el VSPackage de control de código fuente. | Código auxiliar de control de código fuente | Obligatorio |
| <xref:EnvDTE.SourceControl> | Esta interfaz se utiliza en Automation. Como tal, solo expone funciones que se pueden ejecutar sin mostrar ninguna interfaz de usuario. | VSPackage de control de código fuente | Opcional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> | Esta interfaz se usa para guardar la configuración del control de código fuente en el archivo de solución (. sln). La configuración incluye las marcas Ubicación del control de código fuente y estado del control de código fuente. | VSPackage de control de código fuente | Recomendado |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> | Esta interfaz se usa para guardar la configuración del control de código fuente en el archivo de opciones de solución (. suo). Esto puede incluir la configuración de control de código fuente específica del usuario, como la ubicación de inscripción del usuario actual. | VSPackage de control de código fuente | Recomendado |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> | Esta interfaz se usa para supervisar eventos a fin de realizar operaciones como la protección de archivos de proyecto antes de cerrar soluciones u obtener nuevos archivos del control de código fuente al abrir un proyecto. | VSPackage de control de código fuente | Recomendado |

## <a name="see-also"></a>Vea también
- [Elementos de diseño](../../extensibility/internals/source-control-vspackage-design-elements.md)
