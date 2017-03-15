---
title: "Estructura de VSPackage (VSPackage del Control de c&#243;digo fuente) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPackages, estructura"
  - "paquetes de control de código fuente, información general de VSPackage"
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
caps.latest.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 26
---
# Estructura de VSPackage (VSPackage del Control de c&#243;digo fuente)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

El SDK de paquete de Control de origen proporciona directrices para crear un VSPackage que permiten un implementador de control de código fuente para integrar su funcionalidad de control de código fuente con el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno. Un VSPackage es un componente COM que normalmente se carga a petición mediante el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el entorno de desarrollo integrado \(IDE\) se basa en los servicios que se anuncian en el paquete en sus entradas del registro. Debe implementar cada VSPackage la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>. Normalmente, un paquete VSPackage consume servicios ofrecidos por la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE y proffers algunos servicios propios.  
  
 Un VSPackage declara sus elementos de menú y establece un estado de elemento predeterminado mediante el archivo .vsct. El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE muestra los elementos de menú en este estado hasta que se cargue el paquete VSPackage. Posteriormente, la implementación de VSPackage de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> se invoca para habilitar o deshabilitar elementos de menú.  
  
## Características del paquete de Control de código fuente  
 Un control de código fuente VSPackage está muy integrado en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 La semántica de VSPackage incluye:  
  
-   Interfaz que se implementa en virtud de un VSPackage \(el `IVsPackage` interfaz\)  
  
-   Implementación de comandos de la interfaz de usuario \(archivo .vsct y la implementación de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz\)  
  
-   Registro de VSPackage con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 El VSPackage del control de código fuente debe comunicarse con estas otras [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entidades:  
  
-   Proyectos  
  
-   Editores  
  
-   Soluciones  
  
-   Windows  
  
-   La tabla del documento de ejecución  
  
### Servicios de entorno de Visual Studio que pueden consumir  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 Servicio de SVsRegisterScciProvider  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>  
  
### Interfaces VSIP implementado y llamado  
 Un paquete de control de código fuente es un VSPackage y, por tanto, puede interactuar directamente con otros VSPackages que están registrados con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Para proporcionar la gran variedad de funcionalidad de control de código fuente, puede tratar un control de código fuente VSPackage con interfaces proporcionadas por los proyectos o el shell.  
  
 Todos los proyectos de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debe implementar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> se reconozca como un proyecto dentro de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Sin embargo, no está especializada en esta interfaz suficiente para el control de código fuente. Proyectos que se esperan que esté en el origen de control de implementar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>. Esta interfaz se utiliza el control de código fuente VSPackage para consultar un proyecto para su contenido y proporcionarla glifos e información de enlace \(es decir, la información necesaria para establecer una conexión entre la ubicación del servidor y la ubicación del disco de un proyecto que está bajo control de código fuente\).  
  
 El control de código fuente VSPackage implementa el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, que a su vez permite a los proyectos que se registran para el control de código fuente y recuperar su estado de glifos.  
  
 Para obtener una lista completa de interfaces que debe tener en cuenta un VSPackage del control de código fuente, consulte [Interfaces y servicios relacionados](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md).  
  
## Vea también  
 [Elementos de diseño](../../extensibility/internals/source-control-vspackage-design-elements.md)   
 [Interfaces y servicios relacionados](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)