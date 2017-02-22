---
title: "Utilizar y proporcionar servicios | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ejemplos [Visual Studio SDK], servicios"
  - "Servicios de Visual Studio"
  - "servicios"
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
caps.latest.revision: 41
caps.handback.revision: 41
ms.author: "gregvanl"
manager: "ghogen"
---
# Utilizar y proporcionar servicios
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un servicio es un contrato entre dos VSPackages. Un VSPackage ofrece un conjunto específico de interfaces para otro VSPackage consumir. Por ejemplo, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ofrece el <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> servicio a cualquier VSPackage se carga. Este servicio proporciona la <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interfaz, que puede utilizarse para escribir en el registro de actividad. Para obtener más información, consulta [Cómo: utilizar el registro de actividad](../extensibility/how-to-use-the-activity-log.md).  
  
 VSPackages puede ofrecer servicios de su cuenta desde el <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> interfaz...  
  
 Visual Studio ofrece servicios importantes, como los siguientes:  
  
|Servicio IDE|Descripción|  
|------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Proporciona acceso a IDE servicios tratar con la funcionalidad básica, VSPackages y el registro.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Proporciona ventanas básica y la funcionalidad relacionada con la interfaz de usuario en el IDE, como la capacidad para crear herramientas y ventanas de documento.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Proporciona funciones básicas relacionadas con la solución, como la capacidad de enumerar los proyectos, crear nuevos proyectos y supervisar los cambios en el proyecto.|  
  
## En esta sección  
 [Fundamentos del servicio](../extensibility/internals/service-essentials.md)  
 Presenta los elementos importantes de un servicio de Visual Studio.  
  
 [Cómo: obtener un servicio](../extensibility/how-to-get-a-service.md)  
 Describe cómo solicitar \(consumir\) un servicio.  
  
 [Cómo: proporcionar un servicio](../extensibility/how-to-provide-a-service.md)  
 Explica cómo proporcionar un servicio.  
  
 [Cómo: proporcionar un servicio asincrónico de Visual Studio](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md)  
 Explica cómo proporcionar un servicio asincrónico.  
  
 [Cómo: solucionar problemas de servicios](../extensibility/how-to-troubleshoot-services.md)  
 Se describen problemas comunes y ofrece soluciones a ellos.  
  
## Secciones relacionadas  
 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)