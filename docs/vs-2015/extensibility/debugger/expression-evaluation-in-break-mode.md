---
title: Evaluación de expresiones en modo de interrupción | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 362e50e20519c358564d13ba169f706fe384ca5c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152758"
---
# <a name="expression-evaluation-in-break-mode"></a>Evaluación de expresiones en el modo de interrupción
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A continuación se describe el proceso que se produce cuando el depurador está en modo de interrupción y debe realizar la evaluación de expresiones.  
  
## <a name="expression-evaluation-process"></a>Proceso de evaluación de expresiones  
 Estos son los pasos básicos necesarios para evaluar una expresión:  
  
1. El administrador de depuración de sesión (SDM) llama a [IDebugStackFrame2:: GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) para obtener una interfaz de contexto de expresión, [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md).  
  
2. Después, el SDM llama a [IDebugExpressionContext2::P arsetext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) con la cadena que se va a analizar.  
  
3. Si ParseText no Devuelve S_OK, se devuelve la razón del error.  
  
     casos  
  
     Si ParseText Devuelve S_OK, el SDM puede llamar a [IDebugExpression2:: EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) para obtener un valor final de la expresión analizada.  
  
    - En el caso de usar `IDebugExpression2::EvaluateSync` , se usa la interfaz de devolución de llamada especificada para comunicar el proceso en curso de la evaluación. El valor final se devuelve en una interfaz [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) .  
  
    - En el caso de usar `IDebugExpression2::EvaluateAsync` , se usa la interfaz de devolución de llamada especificada para comunicar el proceso en curso de la evaluación. Una vez completada la evaluación, EvaluateAsync envía una interfaz [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) a través de la devolución de llamada. Con esta interfaz de eventos, el valor final se puede obtener con [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md).  
  
## <a name="see-also"></a>Consulte también  
 [Llamada a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)
