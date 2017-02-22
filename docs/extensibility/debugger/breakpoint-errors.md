---
title: "Errores de punto de interrupci&#243;n | Microsoft Docs"
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
  - "puntos de interrupción, errores"
  - "depurar [SDK de depuración], errores de punto de interrupción"
  - "errores [SDK de depuración]"
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# Errores de punto de interrupci&#243;n
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

A continuación se describe el proceso cuando un punto de interrupción intenta vincular al código pero a los errores:  
  
## Solucionar problemas de un error de punto de interrupción  
  
1.  El motor de depuración \(DE\) envía [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) el administrador de depuración de la sesión \(SDM\).  
  
2.  El SDM llama [IDebugBreakpointErrorEvent2:: GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) \(IDebugErrorBreakpoint2 \*\* `ppErrorBP`\) para obtener el punto de interrupción del error.  
  
3.  El SDM llama [IDebugErrorBreakpoint2:: GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md) para obtener el punto de interrupción pendiente de que el punto de interrupción de error originado.  
  
4.  El SDM llama [IDebugErrorBreakpoint2:: GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) para obtener la razón por la que el punto de interrupción de error no se para enlazar.  
  
## Vea también  
 [Llamar a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)