---
title: "Evaluaci&#243;n de expresiones en el modo de interrupci&#243;n | Microsoft Docs"
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
  - "modo de interrupción, la evaluación de expresiones"
  - "depurar [SDK de depuración], la evaluación de expresiones"
  - "evaluación de expresiones, el modo de interrupción"
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Evaluaci&#243;n de expresiones en el modo de interrupci&#243;n
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

A continuación se describe el proceso que se produce cuando el depurador está en modo de interrupción y debe realizar la evaluación de la expresión.  
  
## Proceso de evaluación de expresiones  
 Estos son los pasos básicos relacionados con la evaluación de una expresión:  
  
1.  El administrador de depuración de sesión \(SDM\) llama a [IDebugStackFrame2:: GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) para obtener una interfaz de contexto de la expresión, [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md).  
  
2.  El SDM llama [IDebugExpressionContext2:: ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) con la cadena que se va a analizar.  
  
3.  Si ParseText no devuelve S\_OK, el motivo del error se devuelve.  
  
     \- si no  
  
     Si ParseText devuelve S\_OK, el SDM puede llamar [IDebugExpression2:: EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) para obtener un valor final de la expresión analizada.  
  
    -   En el caso de uso `IDebugExpression2::EvaluateSync`, la interfaz de devolución de llamada especificada se utiliza para comunicar el proceso actual de evaluación.  el valor final se devuelve en una interfaz de [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) .  
  
    -   En el caso de uso `IDebugExpression2::EvaluateAsync`, la interfaz de devolución de llamada especificada se utiliza para comunicar el proceso actual de evaluación.  Una vez completada la evaluación, EvaluateAsync envía una interfaz de [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) con la devolución de llamada.  Con esta interfaz de eventos, el valor final se puede obtener con [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md).  
  
## Vea también  
 [Llamar a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)