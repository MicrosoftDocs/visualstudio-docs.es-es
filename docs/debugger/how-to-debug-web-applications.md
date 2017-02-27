---
title: "C&#243;mo: Depurar aplicaciones web | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "Formularios Web Forms de ASP.NET, depurar"
  - "ASP.NET, depurar aplicaciones web"
  - "depurar aplicaciones web ASP.NET, durante el desarrollo"
  - "servicios Web, depurar"
ms.assetid: 6440d12e-6b29-42c5-a958-99aeaaff480f
caps.latest.revision: 37
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 37
---
# C&#243;mo: Depurar aplicaciones web
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] es la principal tecnología que se usa para desarrollar aplicaciones web en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  El depurador de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proporciona herramientas muy eficaces para depurar aplicaciones web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] localmente o en un servidor remoto.  En este tema se describe cómo depurar un proyecto [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] durante el desarrollo.  Para obtener información sobre cómo depurar una aplicación web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ya implementada en un servidor de producción, vea [Depurar aplicaciones web implementadas](../debugger/debugging-deployed-web-applications.md).  
  
 Para depurar una aplicación [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]:  
  
-   Debe tener los permisos necesarios.  Para obtener más información, vea [Requisitos del sistema](../debugger/aspnet-debugging-system-requirements.md).  
  
-   La depuración [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] se debe habilitar en **Propiedades del proyecto**.  
  
-   El archivo de configuración de la aplicación \(Web.config\) se debe establecer en modo de depuración.  El modo de depuración hace que [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] genere símbolos para los archivos generados dinámicamente y permite al depurador asociarse a la aplicación [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] establece esto automáticamente al empezar a depurar si se creó el proyecto a partir de la plantilla de proyectos web.  
  
-   Para obtener más información, vea [Cómo: Habilitar la depuración de aplicaciones de ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md).  
  
### Para depurar una aplicación Web durante la fase de desarrollo  
  
1.  En el menú **Depurar**, haga clic en **Inicio** para comenzar la depuración de la aplicación web.  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] compila el proyecto de aplicación web, implementa la aplicación si es necesario, inicia el Servidor de desarrollo de ASP.NET si se está depurando localmente y lo asocia al proceso de trabajo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
2.  Utilice el depurador para establecer y borrar puntos de interrupción, ver paso a paso el código y realizar otras operaciones de depuración, igual que haría para cualquier otra aplicación.  
  
     Para obtener más información, vea [Conceptos básicos del depurador](../debugger/debugger-basics.md).  
  
3.  En el menú **Depurar**, haga clic en **Detener depuración** para finalizar la sesión de depuración, o bien, en el menú **Archivo** en Internet Explorer, haga clic en **Cerrar**.  
  
## Vea también  
 [Depurar script y aplicaciones web](../debugger/debugging-web-applications-and-script.md)   
 [Depurar aplicaciones ASP.NET y aplicaciones habilitadas para AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Cómo: Habilitar la depuración de aplicaciones de ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)