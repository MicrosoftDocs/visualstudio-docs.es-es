---
title: "Depurar aplicaciones ASP.NET y aplicaciones habilitadas para AJAX | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurar [ASP.NET], acerca de la depuración de ASP.NET"
  - "depurar aplicaciones web ASP.NET"
  - "depurar, WCF"
  - "WCF, depurar"
ms.assetid: 9d531913-541b-47b8-864d-138021fca0c6
caps.latest.revision: 31
caps.handback.revision: 31
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Depurar aplicaciones ASP.NET y aplicaciones habilitadas para AJAX
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Depurar las aplicaciones web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] es similar a depurar un Windows Form o cualquier otra aplicación para Windows porque ambos tipos de aplicación implican controles y eventos.  No obstante, hay también diferencias básicas entre ambos tipos de aplicación:  
  
-   El seguimiento del estado es más complejo en una aplicación Web.  
  
-   En una aplicación para Windows, el código que se va a depurar está principalmente en una única ubicación; en una aplicación web, el código puede estar en el cliente y en el servidor.  Mientras que el código [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] se encuentra por completo en el servidor, también podría haber código de JavaScript o de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] en el cliente.  
  
## En esta sección  
 [Preparar la depuración en ASP.NET](../debugger/preparing-to-debug-aspnet.md)  
 Se describen los pasos necesarios para habilitar la depuración de las aplicaciones [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
 [Depurar aplicaciones web](../debugger/debugging-web-applications.md)  
 Se explica cómo depurar una aplicación [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], incluidas las aplicaciones de script habilitadas para AJAX.  
  
## Secciones relacionadas  
 [Administración de excepciones con el depurador](../debugger/managing-exceptions-with-the-debugger.md)  
 Se explica por qué Sólo mi código se debe habilitar para depurar excepciones de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
 [Debugging and Tracing Ajax Applications Overview](../Topic/Debugging%20and%20Tracing%20Ajax%20Applications%20Overview.md)  
 Explica algunas técnicas y herramientas que pueden ayudarle a depurar su código AJAX.  
  
 [Uso de IntelliTrace](../debugger/intellitrace.md)  
 Depure el código con más rapidez mediante IntelliTrace para registrar y revisar un historial del estado de la aplicación sin reiniciar la aplicación con tanta frecuencia.  Puede ver información sobre los eventos y las llamadas que se producen durante la ejecución de la aplicación e iniciar la depuración desde esos puntos en el tiempo.  Requiere Visual Studio Ultimate.  
  
## Vea también  
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Depurar script y aplicaciones web](../debugger/debugging-web-applications-and-script.md)   
 [Preparación y configuración de la depuración](../debugger/debugger-settings-and-preparation.md)   
 [Conceptos básicos del depurador](../debugger/debugger-basics.md)