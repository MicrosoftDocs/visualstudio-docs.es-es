---
title: "Crear un punto de interrupci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "puntos de interrupción, crear"
  - "depurar [SDK de depuración], creación de puntos de interrupción"
ms.assetid: 6f9f87bb-192e-45e0-9a7a-ffe729e87f7d
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Crear un punto de interrupci&#243;n
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

A continuación se describe el proceso de crear un punto de interrupción.  
  
## Métodos en el punto de interrupción Creación  
 Cuando el módulo que es necesario enlazar un punto de interrupción cargado, el administrador de depuración de sesión \(SDM\) llama a los métodos siguientes:  
  
1.  [IDebugPendingBreakpoint2:: Habilitar](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)  
  
2.  [IDebugPendingBreakpoint2:: Virtualize](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)  
  
3.  [IDebugPendingBreakpoint2:: CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)  
  
    > [!NOTE]
    >  Se llama**CanBind** cuando un usuario hace un punto de interrupción en la ventana puntos de interrupción.  
  
4.  [IDebugPendingBreakpoint2:: enlace](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)  
  
5.  [IDebugPendingBreakpoint2:: EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)  
  
## Vea también  
 [Llamar a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)