---
title: "Error: No se puede ir al servidor autom&#225;ticamente | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.causality_no_server_response"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depuración remota, error de notificación"
ms.assetid: 9a370ccc-d358-429c-b285-9b6c0649bc68
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Error: No se puede ir al servidor autom&#225;ticamente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El error reza como sigue:  
  
 No se puede ir al servidor automáticamente. El depurador no recibió una notificación antes de que se ejecutase el procedimiento remoto  
  
 Este error puede aparecer cuando intenta ir a un servicio Web \(vea [Ejecutar paso a paso un servicio Web XML](http://msdn.microsoft.com/es-es/8e67de38-bf5f-41cc-a457-1b88ce63d764)\). Puede producirse cuando [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] no se configura correctamente.  
  
 Las posibles causas son:  
  
-   No se ha establecido la depuración en "true" en el archivo web.config de la aplicación [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] \(vea [Modo de depuración en aplicaciones ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)\).  
  
-   Se instaló una versión de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] después de instalar Visual Studio.[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] debe instalarse antes que Visual Studio. Use el **Panel de control** de Windows, **Programas y características** para reparar su instalación de Visual Studio.  
  
## Vea también  
 [Errores de la depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Depuración remota](../debugger/remote-debugging.md)