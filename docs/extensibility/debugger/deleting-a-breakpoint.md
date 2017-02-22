---
title: "Eliminar un punto de interrupci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "puntos de interrupción, eliminar"
  - "depurar [SDK de depuración], eliminar los puntos de interrupción"
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# Eliminar un punto de interrupci&#243;n
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

A continuación se describe el proceso al eliminar un punto de interrupción pendiente:  
  
## Proceso de eliminación  
 El administrador de depuración de sesión \(SDM\) llama al método de [IDebugPendingBreakpoint2:: Eliminar](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) para quitar el punto de interrupción pendiente y todos los puntos de interrupción enlazados enlazados de.  
  
> [!NOTE]
>  Un único punto de interrupción enlazado se puede eliminar también por una llamada a [IDebugBoundBreakpoint2:: Eliminar](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).  
  
## Vea también  
 [Llamar a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)