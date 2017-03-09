---
title: "Requisitos previos para la depuraci&#243;n remota de aplicaciones web | Microsoft Docs"
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
  - "depurar aplicaciones web ASP.NET, servidores remotos"
  - "depuración remota, requisitos previos"
  - "servidores remotos, depurar aplicaciones web"
ms.assetid: 1cd777b5-6d20-4ca6-a0df-51653b118469
caps.latest.revision: 27
caps.handback.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Requisitos previos para la depuraci&#243;n remota de aplicaciones web
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Con el depurador de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], puede depurar una aplicación web de modo transparente en el equipo local o en un servidor remoto.  Esto significa que el depurador funciona del mismo modo y permite usar las mismas características en cualquiera de los dos equipos.  No obstante, para que la depuración remota funcione correctamente, se deben cumplir algunos requisitos previos.  
  
-   Los componentes de depuración remota de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] se deben instalar en el servidor que desee depurar.  Para obtener más información, vea [Configurar la depuración remota](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md).  
  
-   De forma predeterminada, el proceso de trabajo de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] se ejecuta como un proceso de usuario de ASPNET.  Por lo tanto, debe tener privilegios de administrador en el equipo en el que se ejecute [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] para depurarlo.  El nombre del proceso de trabajo de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] varía en función del escenario de depuración y de la versión de IIS.  Para obtener más información, vea [Cómo: Buscar el nombre de un proceso de ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md).  
  
## Vea también  
 [Depurar aplicaciones ASP.NET y aplicaciones habilitadas para AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Requisitos del sistema](../debugger/aspnet-debugging-system-requirements.md)