---
title: Uso y provisión de servicios | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
caps.latest.revision: 42
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 189ff14c566c3007810ef35cd63ec03a5958e07c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51779715"
---
# <a name="using-and-providing-services"></a>Uso y prestación de servicios
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un servicio es un contrato entre dos VSPackages. Un VSPackage ofrece un conjunto específico de interfaces para otro paquete de VS consumir. Por ejemplo, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ofrece el <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> atenderla a cualquier VSPackage cargas. Este servicio proporciona la <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interfaz, que puede usarse para escribir en el registro de actividad. Para obtener más información, consulte [Cómo: usar el registro de actividad](../extensibility/how-to-use-the-activity-log.md).  
  
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
  
 [Obtención de un servicio](../extensibility/how-to-get-a-service.md)  
 Se describe cómo solicitar (consumir) un servicio.  
  
 [Provisión de un servicio](../extensibility/how-to-provide-a-service.md)  
 Describe cómo proporcionar un servicio.  
  
 [Provisión de un servicio asincrónico de Visual Studio](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md)  
 Describe cómo proporcionar un servicio asincrónico.  
  
 [Servicios de solución de problemas](../extensibility/how-to-troubleshoot-services.md)  
 Se describen problemas comunes y se presentan soluciones a ellos.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)

