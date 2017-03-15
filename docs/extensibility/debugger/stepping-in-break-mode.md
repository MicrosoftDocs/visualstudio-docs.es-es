---
title: "Ejecuci&#243;n paso a paso en modo de interrupci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modo de interrupción, paso a paso"
  - "ejecución paso a paso en modo de interrupción"
  - "depurar [SDK de depuración], la ejecución paso a paso en modo de interrupción"
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# Ejecuci&#243;n paso a paso en modo de interrupci&#243;n
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

A continuación se describe el proceso que se produce cuando el depurador está en modo de interrupción y debe recorrer el código:  
  
## Proceso de recorrido  
  
1.  Llamada [IDebugProgram2:: paso](../../extensibility/debugger/reference/idebugprogram2-step.md) con argumentos de [STEPKIND](../../extensibility/debugger/reference/stepkind.md) y de [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) para ejecutar un paso.  
  
2.  Cuando finaliza el paso, envíe [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) como evento que detiene.  
  
## Vea también  
 [Llamar a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)