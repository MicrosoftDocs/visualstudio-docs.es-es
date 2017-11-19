---
title: "Evaluación de expresiones en el modo de interrupción | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 766f00475971da1ca009737f9360952422177814
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="expression-evaluation-in-break-mode"></a>Evaluación de expresiones en el modo de interrupción
A continuación describe el proceso que se produce cuando el depurador está en modo de interrupción y debe realizar la evaluación de expresión.  
  
## <a name="expression-evaluation-process"></a>Proceso de evaluación de expresión  
 Estos son los pasos básicos necesarios para evaluar una expresión:  
  
1.  El Administrador de sesión de depuración (SDM) llama [IDebugStackFrame2::GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) para obtener una interfaz de contexto de la expresión, [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md).  
  
2.  El SDM, a continuación, llama [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) con la cadena se analizará.  
  
3.  Si ParseText no devuelve S_OK, se devuelve el motivo del error.  
  
     -en caso contrario-  
  
     Si ParseText devuelve S_OK, el SDM, a continuación, puede llamar [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) para obtener un valor final de la expresión analizada.  
  
    -   En el caso de uso de `IDebugExpression2::EvaluateSync`, la interfaz de devolución de llamada especificado se usa para comunicar el proceso continuo de la evaluación. Se devuelve el valor final en un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfaz.  
  
    -   En el caso de uso de `IDebugExpression2::EvaluateAsync`, la interfaz de devolución de llamada especificado se usa para comunicar el proceso continuo de la evaluación. Una vez completada la evaluación, EvaluateAsync envía una [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) interfaz a través de la devolución de llamada. Con esta interfaz de eventos, se puede obtener el valor final con [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md).  
  
## <a name="see-also"></a>Vea también  
 [Llamada a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)