---
title: Evaluación de expresiones en modo de interrupción | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc09fc43bd9f0edea4f6dc32e5f37c387c045796
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738721"
---
# <a name="expression-evaluation-in-break-mode"></a>Evaluación de expresiones en modo de interrupción
En la siguiente sección se describe el proceso que se produce cuando el depurador está en modo de interrupción y debe realizar la evaluación de expresiones.

## <a name="expression-evaluation-process"></a>Proceso de evaluación de expresiones
 A continuación se indican los pasos básicos necesarios para evaluar una expresión:

1. El administrador de depuración de sesión (SDM) llama a [IDebugStackFrame2:: GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) para obtener una interfaz de contexto de expresión, [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md).

2. Después, el SDM llama a [IDebugExpressionContext2::P arsetext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) con la cadena que se va a analizar.

3. Si ParseText no Devuelve S_OK, se devuelve la razón del error.

     casos

     Si ParseText Devuelve S_OK, el SDM puede llamar a [IDebugExpression2:: EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) para obtener un valor final de la expresión analizada.

    - Al usar `IDebugExpression2::EvaluateSync` , la interfaz de devolución de llamada dada comunica el proceso en curso de la evaluación. El valor final se devuelve en una interfaz [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) .

    - Al usar `IDebugExpression2::EvaluateAsync` , la interfaz de devolución de llamada dada comunica el proceso en curso de la evaluación. Una vez completada la evaluación, EvaluateAsync envía una interfaz [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) a través de la devolución de llamada. Con esta interfaz de eventos, el valor final da como resultado [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md).

## <a name="see-also"></a>Vea también
- [Llamar a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)
