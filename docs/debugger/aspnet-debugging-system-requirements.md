---
title: "Depuraci&#243;n ASP.NET: requisitos del sistema | Microsoft Docs"
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
  - "depurar aplicaciones web ASP.NET, requisitos del sistema"
  - "depurar aplicaciones web ASP.NET, requisitos de seguridad"
ms.assetid: 7810b9b2-debf-4271-8fc7-1df031123255
caps.latest.revision: 38
caps.handback.revision: 38
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Depuraci&#243;n ASP.NET: requisitos del sistema
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En este tema se describen los requisitos de software y seguridad de los escenarios de depuración de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]:  
  
-   Depuración local, en la que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y la aplicación web se ejecutan en el mismo equipo. Existen dos versiones de este escenario:  
  
    -   El código de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] reside en el sistema de archivos.  
  
    -   El código de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] reside en un sitio web de IIS.  
  
-   La depuración remota, en la que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] se ejecuta en un equipo cliente y depura una aplicación web que se está ejecutando en un equipo servidor remoto.  
  
## Requisitos de seguridad  
 Para la depuración remota, los equipos locales y remotos deben estar en una configuración de dominio o una configuración de grupo de trabajo.  
  
 Para depurar el proceso de trabajo de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], debe tener permiso para depurar dicho proceso. De forma predeterminada, las aplicaciones de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] se ejecutan como el usuario **ASPNET**. Si el proceso de trabajo se ejecuta con la cuenta **ASPNET** o **NETWORK SERVICE**, deberá tener privilegios de administrador para depurarlo.  
  
 El nombre del proceso de trabajo de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] varía en función del escenario de depuración y de la versión de IIS. Para obtener más información, consulta [Cómo: Buscar el nombre de un proceso de ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md).  
  
 Puede cambiar la cuenta de usuario en la que se ejecuta el proceso de trabajo de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] editando el archivo machine.config en el servidor que ejecuta IIS. La mejor manera de hacerlo es mediante el **Administrador de Internet Information Services \(IIS\)**. Para obtener más información, consulta [Cómo: Ejecutar el proceso de trabajo en una cuenta de usuario](../debugger/how-to-run-the-worker-process-under-a-user-account.md).  
  
 Si cambia el proceso de trabajo de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] para que se ejecute en su propia cuenta de usuario, no tiene porqué ser administrador en el servidor que esté ejecutando IIS.  
  
> [!CAUTION]
>  Antes de cambiar el proceso de trabajo de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] para que se ejecute en una cuenta diferente, tenga en cuenta las posibles consecuencias de que el proceso de trabajo de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pudiera sufrir intrusiones mientras se ejecute en dicha cuenta. Las cuentas de usuario ASPNET y NETWORK SERVICE se ejecutan con permisos mínimos, lo que reduce los posibles daños si el proceso sufre alguna intrusión. Si debe cambiar el proceso de trabajo de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] para que se ejecute en una cuenta que tenga permisos superiores, el daño puede ser mayor.  
  
## Vea también  
 [Depurar aplicaciones ASP.NET y aplicaciones habilitadas para AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Cómo: Ejecutar el proceso de trabajo en una cuenta de usuario](../debugger/how-to-run-the-worker-process-under-a-user-account.md)