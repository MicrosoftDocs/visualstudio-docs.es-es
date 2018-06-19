---
title: Uso y proporciona servicios | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 351b5b5c0ab32ab7e8267864eddaae10459a23bd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138345"
---
# <a name="using-and-providing-services"></a>Uso y proporciona servicios
Un servicio es un contrato entre dos VSPackages. Un VSPackage ofrece un conjunto específico de interfaces para otro VSPackage consumir. Por ejemplo, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ofrece el <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> servicio a cualquier VSPackage se carga. Este servicio proporciona la <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interfaz, que se puede usar para escribir en el registro de actividad. Para obtener más información, consulte [Cómo: usar el registro de actividad](../extensibility/how-to-use-the-activity-log.md).  
  
 VSPackages puede ofrecer servicios de su cuenta desde la <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> interfaz...  
  
 Visual Studio ofrece servicios importantes, como las siguientes:  
  
|Servicio IDE|Descripción|  
|-----------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Proporciona acceso al IDE de servicios de tratar con la funcionalidad básica, VSPackages y el registro.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Proporciona básica basada en ventanas y funcionalidad relacionada con la interfaz de usuario en el IDE, como la capacidad para crear herramientas y ventanas de documento.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Proporciona funciones básicas relacionadas con la solución, como la capacidad para enumerar los proyectos, crear nuevos proyectos y supervisar cambios en el proyecto.|  
  
## <a name="in-this-section"></a>En esta sección  
 [Conceptos básicos del servicio](../extensibility/internals/service-essentials.md)  
 Presenta los elementos importantes de un servicio de Visual Studio.  
  
 [Obtención de un servicio](../extensibility/how-to-get-a-service.md)  
 Describe cómo solicitar (consumir) un servicio.  
  
 [Provisión de un servicio](../extensibility/how-to-provide-a-service.md)  
 Describe cómo proporcionar un servicio.  
  
 [Provisión de un servicio asincrónico de Visual Studio](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md)  
 Describe cómo proporcionar un servicio asincrónico.  
  
 [Servicios de solución de problemas](../extensibility/how-to-troubleshoot-services.md)  
 Describe los problemas comunes y se presentan soluciones a ellos.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)