---
title: "Terminar un programa | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "programas, eventos de finalización"
  - "depurar [SDK de depuración], terminar un programa"
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# Terminar un programa
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

A continuación se ofrece una descripción de la finalización de un único programa de un subproceso.  
  
## Proceso de finalización  
  
1.  El OF envía [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) con [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)válido.  
  
2.  El OF envía [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) con [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)válido.  
  
 El IDE entra en el modo de diseño.  Las llamadas [IDebugPortNotify2:: RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) de motor o del entorno en tiempo de ejecución de depuración para quitar el programa de puerto.  
  
## Vea también  
 [Llamar a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)