---
title: Uso y provisión de servicios | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e58ace81dbf3b39ed9e7707a50c1f7beae35e88f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54989278"
---
# <a name="using-and-providing-services"></a>Uso y prestación de servicios
Un servicio es un contrato entre dos VSPackages. Un VSPackage ofrece un conjunto específico de interfaces para otro paquete de VS consumir. Por ejemplo, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ofrece el <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> atenderla a cualquier VSPackage cargas. Este servicio proporciona la <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interfaz, que puede usarse para escribir en el registro de actividad. Para obtener más información, vea [Cómo: Usar el registro de actividad](../extensibility/how-to-use-the-activity-log.md).  
  
 Los paquetes VSPackage pueden ofrecer servicios de su cuenta desde la <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> interfaz...  
  
 Visual Studio ofrece servicios importantes, como las siguientes:  
  
|Servicio IDE|Descripción|  
|-----------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Proporciona acceso al IDE de servicios de tratar con funcionalidad básica, VSPackages y el registro.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Proporciona básica basada en ventanas y funcionalidad relacionada con la interfaz de usuario en el IDE, como la capacidad para crear herramientas y ventanas de documento.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Proporciona funciones básicas relacionadas con la solución, como la capacidad para enumerar los proyectos, crear nuevos proyectos y supervisar los cambios del proyecto.|  
  
## <a name="in-this-section"></a>En esta sección  
 [Conceptos básicos del servicio](../extensibility/internals/service-essentials.md)  
 Presenta los elementos importantes de un servicio de Visual Studio.  
  
 [Cómo: Obtener un servicio](../extensibility/how-to-get-a-service.md)  
 Se describe cómo solicitar (consumir) un servicio.  
  
 [Cómo: Proporcionar un servicio](../extensibility/how-to-provide-a-service.md)  
 Describe cómo proporcionar un servicio.  
  
 [Cómo: Proporciona un servicio asincrónico de Visual Studio](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md)  
 Describe cómo proporcionar un servicio asincrónico.  
  
 [Cómo: Solucionar problemas de servicios](../extensibility/how-to-troubleshoot-services.md)  
 Se describen problemas comunes y se presentan soluciones a ellos.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)