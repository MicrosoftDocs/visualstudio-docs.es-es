---
title: Evaluación de expresiones en modo de interrupción ? Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738721"
---
# <a name="expression-evaluation-in-break-mode"></a>Evaluación de expresiones en modo de interrupción
En la siguiente sección se describe el proceso que se produce cuando el depurador está en modo de interrupción y debe llevar a cabo la evaluación de expresiones.

## <a name="expression-evaluation-process"></a>Proceso de evaluación de expresiones
 A continuación se indican los pasos básicos implicados en la evaluación de una expresión:

1. El Administrador de depuración de sesión (SDM) llama a [IDebugStackFrame2::GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) para obtener una interfaz de contexto de expresión, [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md).

2. A continuación, el SDM llama a [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) con la cadena que se va a analizar.

3. Si ParseText no devuelve S_OK, se devuelve el motivo del error.

     -de lo contrario-

     Si ParseText devuelve S_OK, el SDM puede llamar a [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) para obtener un valor final de la expresión analizada.

    - Cuando `IDebugExpression2::EvaluateSync`se utiliza , la interfaz de devolución de llamada dada comunica el proceso en curso de la evaluación. El valor final se devuelve en un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfaz.

    - Cuando `IDebugExpression2::EvaluateAsync`se utiliza , la interfaz de devolución de llamada dada comunica el proceso en curso de la evaluación. Una vez completada la evaluación, EvaluateAsync envía una interfaz [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) a través de la devolución de llamada. Con esta interfaz de eventos, el valor final se produce con [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md).

## <a name="see-also"></a>Vea también
- [Eventos del depurador de llamadas](../../extensibility/debugger/calling-debugger-events.md)
