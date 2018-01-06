---
title: "Estructura de VSPackage (VSPackage de Control de código fuente) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
caps.latest.revision: "26"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 168aa0f7b93d20afaa30924dc17f05e0cac465bb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="vspackage-structure-source-control-vspackage"></a>Estructura de VSPackage (VSPackage de Control de código fuente)
El SDK de paquete de Control de código fuente proporciona instrucciones para crear un VSPackage que permiten un implementador de control de código fuente para integrar su funcionalidad de control de código fuente con el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno. Un VSPackage es un componente COM que normalmente se carga a petición mediante el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el entorno de desarrollo integrado (IDE) en función de los servicios que se anuncian el paquete en sus entradas del registro. Cada VSPackage debe implementar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>. Un VSPackage normalmente consume servicios ofrecidos por el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE y proffers algunos servicios de su propio.  
  
 Un VSPackage declara sus elementos de menú y establece un estado de elemento predeterminado mediante el archivo .vsct. El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE muestra los elementos de menú en este estado hasta que se cargue el VSPackage. Posteriormente, la implementación que hace VSPackage de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método se llama para habilitar o deshabilitar elementos de menú.  
  
## <a name="source-control-package-characteristics"></a>Características del paquete de Control de código fuente  
 Un control de código fuente VSPackage está totalmente integrado en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 La semántica de VSPackage incluye:  
  
-   Interfaz que se implementa en virtud de un paquete VSPackage (el `IVsPackage` interfaz)  
  
-   Implementación de comandos de la interfaz de usuario (archivo .vsct y la implementación de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz)  
  
-   Registro del VSPackage con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 El control de código fuente VSPackage debe comunicarse con estos otros [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entidades:  
  
-   Proyectos  
  
-   Editores  
  
-   Soluciones  
  
-   Windows  
  
-   La tabla document ejecución  
  
### <a name="visual-studio-environment-services-that-may-be-consumed"></a>Servicios de entorno de Visual Studio que se pueden utilizar  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 Servicio de SVsRegisterScciProvider  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>  
  
### <a name="vsip-interfaces-implemented-and-called"></a>Interfaces VSIP implementado y llamado  
 Un paquete de control de código fuente es un paquete VSPackage y, por lo tanto, puede interactuar directamente con otros VSPackages que están registrados con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Para proporcionar la gama completa de la funcionalidad de control de código fuente, un control de código fuente VSPackage puede tratar con interfaces proporcionadas por el comando de shell o los proyectos.  
  
 Todos los proyectos de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debe implementar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> se reconozca como un proyecto dentro de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Sin embargo, esta interfaz no está especializada suficiente para el control de código fuente. Proyectos que se esperan que estuvieran en el origen de control de implementar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>. El control de código fuente VSPackage usan esta interfaz para consultar un proyecto para su contenido y proporcionarla glifos e información de enlace (la información necesaria para establecer una conexión entre la ubicación del servidor y la ubicación del disco de un proyecto que está en control de código fuente).  
  
 El control de código fuente VSPackage implementa la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, que a su vez permite a los proyectos que se registran para el control de código fuente y recuperar los glifos de estado.  
  
 Para obtener una lista completa de interfaces que debe tener en cuenta un VSPackage del control de código fuente, consulte [servicios relacionados e Interfaces](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md).  
  
## <a name="see-also"></a>Vea también  
 [Elementos de diseño](../../extensibility/internals/source-control-vspackage-design-elements.md)   
 [Interfaces y servicios relacionados](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)