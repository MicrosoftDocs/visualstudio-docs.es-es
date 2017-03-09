---
title: "Error: El Monitor de depuraci&#243;n remota de Microsoft Visual Studio del equipo remoto se est&#225; ejecutando con un usuario diferente | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "anyuser (opción)"
  - "-anyuser (opción)"
  - "msvsmon.exe"
  - "Monitor de depuración remota"
  - "depuración remota, Monitor de depuración remota"
ms.assetid: e5b18734-2daf-4c58-b5de-24ae1295703e
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Error: El Monitor de depuraci&#243;n remota de Microsoft Visual Studio del equipo remoto se est&#225; ejecutando con un usuario diferente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Al intentar realizar una depuración remota, es posible recibir el siguiente mensaje de error:  
  
 El Monitor de depuración remota de Microsoft Visual Studio del equipo remoto se está ejecutando como usuario distinto.  
  
## Motivo  
 Este mensaje aparece cuando se lleva a cabo la depuración en modo Sin autenticación y el usuario que inició msvsmon no es el usuario que ejecuta Visual Studio.  
  
## Soluciones  
 La solución mejor y más segura es ejecutar el Monitor de depuración remota \(msvsmon.exe\) con la misma cuenta de usuario que Visual Studio.  Si no es posible hacerlo, puede ejecutar el Monitor de depuración remota con otra cuenta activando la opción **Permitir que cualquier usuario depure** en el cuadro de diálogo **Opciones** del Monitor de depuración remota.  
  
> [!CAUTION]
>  Si se concede permiso a otros usuarios para que se conecten, existe la posibilidad de que se conecten accidentalmente a la sesión de depuración remota equivocada.  Llevar a cabo la depuración en modo **Sin autenticación** no es seguro y debe utilizarse con precaución.  
  
 Para obtener más información, vea [Iniciar el Monitor de depuración remota](../Topic/Start%20%20the%20Remote%20Debugging%20Monitor.md).  
  
## Vea también  
 [Errores de la depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Depuración remota](../debugger/remote-debugging.md)