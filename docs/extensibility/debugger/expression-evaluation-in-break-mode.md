---
title: Evaluación de expresiones en modo de interrupción | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 62824c46e682b0418b8797d6adee0b504f04b414
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53987212"
---
# <a name="expression-evaluation-in-break-mode"></a>Evaluación de expresiones en modo de interrupción
La siguiente sección describe el proceso que se produce cuando el depurador está en modo de interrupción y debe llevar a cabo la evaluación de expresiones.  
  
## <a name="expression-evaluation-process"></a>Proceso de evaluación de expresión  
 Estos son los pasos básicos implicados en la evaluación de una expresión:  
  
1.  El Administrador de depuración de la sesión (SDM) llama a [IDebugStackFrame2::GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) para obtener una interfaz de contexto de la expresión, [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md).  
  
2.  A continuación, llama el SDM [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) con la cadena que se va a analizar.  
  
3.  Si ParseText no devuelve S_OK, se devuelve el motivo del error.  
  
     -en caso contrario-  
  
     Si ParseText devuelva S_OK, el SDM, a continuación, puede llamar [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) para obtener un valor final de la expresión analizada.  
  
    -   Cuando se usa `IDebugExpression2::EvaluateSync`, la interfaz de devolución de llamada especificada comunica el proceso de evaluación en curso. Se devuelve el valor final en un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfaz.  
  
    -   Cuando se usa `IDebugExpression2::EvaluateAsync`, la interfaz de devolución de llamada especificada comunica el proceso de evaluación en curso. Una vez completada la evaluación, EvaluateAsync envía un [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) interfaz a través de la devolución de llamada. Con esta interfaz de eventos, el valor final de resultados con [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md).  
  
## <a name="see-also"></a>Vea también  
 [Llamar a los eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)