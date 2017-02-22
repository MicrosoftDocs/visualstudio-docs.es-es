---
title: "Alcanzar un punto de interrupci&#243;n | Microsoft Docs"
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
  - "depurar [SDK de depuración], alcanzar puntos de interrupción"
  - "puntos de interrupción, alcanza"
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# Alcanzar un punto de interrupci&#243;n
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

A continuación se describe el proceso cuando el motor de depuración \(DE\) alcanza un punto de interrupción mientras ejecuta o paso:  
  
## Solucionar problemas de un punto de interrupción de la posición  
  
1.  El OF envía una interfaz de [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) como **EVENT\_SYNCHRONIZATION\_STOP**.  
  
2.  El administrador de depuración de sesión \(SDM\) llama a [IDebugBreakpointEvent2::: EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) para obtener el punto de interrupción que se alcance.  
  
## Vea también  
 [Llamar a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)