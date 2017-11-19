---
title: "Servicios relacionados e Interfaces (VSPackage de Control de código fuente) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control packages, interfaces
- interfaces, source control packages
ms.assetid: 3e96e838-5675-46bb-99cf-40d420086038
caps.latest.revision: "26"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d652db21fb98cbb0f06c2ac5ceec0f8f239beff6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>Servicios relacionados e Interfaces (VSPackage de Control de código fuente)
Esta sección enumeran todos el origen controlar interfaces relacionadas con el paquete de VS en el [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]. El control de código fuente VSPackage implementa algunas de estas interfaces y otros usa para realizar las tareas de control de código fuente.  
  
## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>Interfaces implementadas por y para VSPackages de Control de código fuente  
 Las interfaces siguientes se describen en la [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], y el control de código fuente VSPackage implementa un subconjunto de ellos dependiendo de su conjunto de características deseadas. Algunas de las interfaces se marcan como requerido y debe ser implementada por cada control de código fuente VSPackage.  
  
 Para las interfaces que implementa un paquete, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proporciona una implementación predeterminada. Tenga en cuenta que la implementación predeterminada está diseñada para el caso cuando no se ha registrado ningún paquete de VS y no se controla ningún proyecto. Un control de origen escritas correctamente VSPackage implementa las interfaces necesarias en lugar de dejar a la implementación predeterminada de estas interfaces.  
  
 Un control de código fuente VSPackage debe implementar un servicio privado que encapsula algunas o todas las interfaces siguientes.  
  
 Las interfaces son:  
  
-   Necesario: La entidad correspondiente (proyecto de control de código fuente VSPackage, código auxiliar de Control de código fuente,) debe implementar la interfaz.  
  
-   Recomendado: La entidad debe implementar esta interfaz; en caso contrario, la funcionalidad de control de código fuente puede ser limitada.  
  
-   Opcional: la entidad puede implementar esta interfaz para proporcionar un conjunto de características más completo.  
  
|Interfaz|Propósito|Implementado por|¿Implementar?|  
|---------------|-------------|--------------------|----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Editores de llamar a esta interfaz antes de modificar o guardar un archivo. El control de código fuente VSPackage puede desproteger el archivo o denegar la operación si se produce un error en la desprotección.|Control de código fuente VSPackage|Se recomienda|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Esta interfaz proporciona funcionalidad de control de código fuente básico para los proyectos, como registrar y anular el registro de los proyectos con control de código fuente y proporciona soporte para los glifos de control de código fuente básico.|Control de código fuente VSPackage|Obligatorio|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Esta interfaz se obtiene de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> mediante la <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> función, o simplemente convirtiendo el objeto que implementa `IVsHierarchy` a `IVsSccProject2`. Se utiliza para obtener los archivos bajo control de código fuente en un proyecto o para que informa el proyecto de la ubicación o el estado de control de código fuente actual.|Proyecto|Obligatorio|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>|El módulo de integración usa esta interfaz para establecer el VSPackage activo actual.|Control de código fuente VSPackage|Obligatorio|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Esta interfaz se basa en un modelo de suscripción. Cualquier VSPackage puede indicar que desea recibir los eventos de documento y tenga en cuenta el shell en eventos que se van a ocurrir. Se implementa y administra [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], que a su vez pasa los eventos que implementa el `IVsTrackProjectDocumentsEvents2` para el VSPackage.|Código auxiliar de Control de código fuente|Obligatorio|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3>|Esta interfaz proporciona procesamiento por lotes, las operaciones de lectura/escritura sincronizado y avanzada `OnQueryAddFiles` método.|Código auxiliar de Control de código fuente|Obligatorio|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|**El Explorador de soluciones** y proyectos llama a esta interfaz cuando se agregan nuevos archivos a los proyectos, o cuando se cambia el nombre o se eliminan de los proyectos de archivos y carpetas. El control de código fuente VSPackage puede desproteger el archivo de proyecto o cancelar la operación.|Control de código fuente VSPackage|Se recomienda|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3>|**El Explorador de soluciones** y proyectos llama a esta interfaz en respuesta a las llamadas realizadas a los métodos de la interfaz IVstrackProjectDocuments3. El control de código fuente VSPackage puede realizar un seguimiento de las operaciones por lotes, sincronizar operaciones de lectura/escritura y trabajar con más avanzados `OnQueryAddFiles` método.|Control de código fuente VSPackage|Se recomienda|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation>|Esta interfaz proporciona la capacidad de administración de la inscripción de los proyectos Web.|Control de código fuente VSPackage|Se recomienda|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip>|Esta interfaz se utiliza para recuperar información sobre herramientas para los archivos controlados por código fuente en los proyectos.|Control de código fuente VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl>|Esta interfaz proporciona compatibilidad con extensiones de espacio de nombres.|Control de código fuente VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution>|El VSPackage usa esta interfaz para integrar una extensión de espacio de nombres en el **New**, **abiertos**, o **guardar** cuadros de diálogo. Por lo tanto, los proyectos pueden automáticamente agrega al control de código fuente durante la creación, o agregar al control de código fuente cuando guarde la operación está en vigor.|Control de código fuente VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>|El VSPackage usa esta interfaz para definir los glifos adicionales como glifos de control de código fuente para los nodos de **el Explorador de soluciones**.|Control de código fuente VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl>|El **agregar** cuadro de diálogo para proyectos Web usa esta interfaz. Proporciona métodos para la exploración de una ubicación de control de código fuente y para abrir un proyecto Web que agregó anteriormente en el repositorio de control de origen en esa ubicación.|Control de código fuente VSPackage|Se recomienda|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>|Esta interfaz proporciona compatibilidad para la carga asincrónica (en segundo plano) de proyectos de control de código fuente.|Control de código fuente VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents>|Esta interfaz permite a los proyectos ver el progreso de la carga asincrónica iniciada por <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>.|Proyecto|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions>|Esta interfaz permite que el IDE consultar el control de origen activo VSPackage. El IDE consulta el valor de configuración de control de código fuente que tienen un significado incluso cuando no hay ningún control de origen activo registrado de VSPackage. Esta interfaz se implementa y administra [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].|Código auxiliar de Control de código fuente|Obligatorio|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>|Esta interfaz se usa para registrar el VSPackage del control de código fuente.|Código auxiliar de Control de código fuente|Obligatorio|  
|<xref:EnvDTE.SourceControl>|Esta interfaz se usa en la automatización. Por lo tanto, expone sólo las funciones que se pueden ejecutar sin mostrar ninguna interfaz de usuario.|Control de código fuente VSPackage|Optional|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>|Esta interfaz se utiliza para guardar el origen de la configuración de control en el archivo de solución (.sln). La configuración incluye la ubicación del control de código fuente y marcas de estado de control de código fuente.|Control de código fuente VSPackage|Se recomienda|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>|Esta interfaz se utiliza para guardar la configuración de control de código fuente en el archivo de solución (.suo) de opciones. Esto puede incluir opciones de control de origen específica del usuario, como ubicación de la inscripción del usuario actual.|Control de código fuente VSPackage|Se recomienda|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>|Esta interfaz se utiliza para supervisar eventos para poder realizar operaciones como la comprobación de archivos de proyecto antes de cerrar soluciones, u obtener nuevos archivos de control de código fuente al abrir un proyecto.|Control de código fuente VSPackage|Se recomienda|  
  
## <a name="see-also"></a>Vea también  
 [Elementos de diseño](../../extensibility/internals/source-control-vspackage-design-elements.md)