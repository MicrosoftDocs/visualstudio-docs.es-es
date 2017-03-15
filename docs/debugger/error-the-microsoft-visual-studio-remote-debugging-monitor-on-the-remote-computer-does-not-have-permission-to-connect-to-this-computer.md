---
title: "Error: El Monitor de depuraci&#243;n remota de Microsoft Visual Studio del equipo remoto no tiene permiso para conectarse a este equipo. | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.access_denied_oncallback"
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
  - "depuración remota, error de versión de Windows"
ms.assetid: ba08a59b-6dbc-4bbc-9c52-379d3bf5241f
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Error: El Monitor de depuraci&#243;n remota de Microsoft Visual Studio del equipo remoto no tiene permiso para conectarse a este equipo.
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este error aparece cuando el usuario que intenta ejecutar el Monitor de depuración remota de Visual Studio \(msvsmon\) no tiene una cuenta en el equipo local.  
  
### Para corregir este problema  
  
-   Agregue una cuenta de usuario al equipo host del depurador de Visual Studio, con el mismo nombre y contraseña que la cuenta de usuario que ejecuta msvsmon en el equipo remoto  
  
     O bien  
  
-   Ejecute msvsmon como un usuario que tiene permiso para llamar en el equipo local.  Esto indica que el usuario debe ser un usuario de dominio y administrador en el equipo de msvsmon.  Puede especificar la cuenta de usuario para ejecutar msvsmon de dos maneras:  
  
    -   Haga clic con el botón secundario en el icono de msvsmon y elija **Ejecutar como** en el menú contextual  
  
     O bien  
  
    -   En el símbolo del sistema, ejecute `runas.exe`.  
  
## Vea también  
 [Depuración remota en dominios](../Topic/Remote%20Debugging%20Across%20Domains.md)   
 [Errores de la depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Depuración remota](../debugger/remote-debugging.md)