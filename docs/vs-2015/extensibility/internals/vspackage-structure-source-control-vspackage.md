---
title: Estructura VSPackage (VSPackage de control de código fuente) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
caps.latest.revision: 27
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 08bb0a296daca0de1c02b905a75fb10ce05f254e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68206003"
---
# <a name="vspackage-structure-source-control-vspackage"></a>Estructura de VSPackage (VSPackage de control de código fuente)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

El SDK del paquete de control de código fuente proporciona instrucciones para crear un VSPackage que permite a un implementador de control de código fuente integrar su funcionalidad de control de código fuente con el [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] entorno. Un VSPackage es un componente COM que normalmente se carga a petición por el [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] entorno de desarrollo integrado (IDE) en función de los servicios anunciados por el paquete en sus entradas del registro. Cada VSPackage debe implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> . Un VSPackage normalmente consume los servicios que ofrece el [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE y ofrece algunos servicios propios.  
  
 Un VSPackage declara sus elementos de menú y establece un estado de elemento predeterminado a través del archivo. Vsct. El [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE muestra los elementos de menú en este estado hasta que se cargue el VSPackage. Posteriormente, se llama a la implementación del <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método del VSPackage para habilitar o deshabilitar elementos de menú.  
  
## <a name="source-control-package-characteristics"></a>Características del paquete de control de código fuente  
 Un VSPackage de control de código fuente está profundamente integrado en [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 La semántica del VSPackage incluye:  
  
- Interfaz que se va a implementar en virtud de ser un VSPackage (la `IVsPackage` interfaz)  
  
- Implementación de comandos de la interfaz de usuario (archivo. Vsct e implementación de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz)  
  
- Registro del VSPackage con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
  El VSPackage de control de código fuente debe comunicarse con estas otras [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] entidades:  
  
- Proyectos  
  
- Editores  
  
- Soluciones  
  
- Windows  
  
- La tabla de documentos en ejecución  
  
### <a name="visual-studio-environment-services-that-may-be-consumed"></a>Servicios de entorno de Visual Studio que se pueden consumir  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 Servicio SVsRegisterScciProvider  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>  
  
### <a name="vsip-interfaces-implemented-and-called"></a>Interfaces VSIP implementadas y llamadas  
 Un paquete de control de código fuente es un VSPackage y, por tanto, puede interactuar directamente con otros VSPackages que se registran con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Con el fin de proporcionar toda la funcionalidad de control de código fuente, un VSPackage de control de código fuente puede tratar con las interfaces proporcionadas por los proyectos o el shell.  
  
 Cada proyecto de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debe implementar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> para que se reconozca como un proyecto en el [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE. Sin embargo, esta interfaz no es lo suficientemente especializada para el control de código fuente. Los proyectos que se espera que estén bajo control de código fuente implementan <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> . Esta interfaz la usa el VSPackage de control de código fuente para consultar su contenido en un proyecto y proporcionar glifos e información de enlace (la información necesaria para establecer una conexión entre la ubicación del servidor y la ubicación del disco de un proyecto que está bajo control de código fuente).  
  
 El VSPackage de control de código fuente implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> , que a su vez permite que los proyectos se registren en el control de código fuente y recuperen sus glifos de estado.  
  
 Para obtener una lista completa de las interfaces que debe tener en cuenta un VSPackage de control de código fuente, vea [servicios e interfaces relacionados](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md).  
  
## <a name="see-also"></a>Consulte también  
 [Elementos de diseño](../../extensibility/internals/source-control-vspackage-design-elements.md)   
 [Interfaces y servicios relacionados](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)
