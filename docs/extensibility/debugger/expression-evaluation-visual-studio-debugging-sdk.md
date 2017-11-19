---
title: "Evaluación de expresiones (depuración SDK de Visual Studio) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c66a6eac74b3d1494a1e98bcb95112c43c4c1bc8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>Evaluación de expresiones (depuración SDK de Visual Studio)
Modo de interrupción, el IDE debe poder evaluar expresiones simples que implican varias variables del programa. Para lograr esto, el motor de depuración (Alemania) debe ser capaz de analizar y evaluar una expresión que se escriban en una de las ventanas del IDE.  
  
 Las expresiones se crean utilizando el [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) método y se representan mediante resultante [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfaz.  
  
 El **IDebugExpression2** interfaz está implementada por las llamadas y DE su **EvalAsync** método para devolver un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfaz para el IDE, con el fin de mostrar el resultados de la evaluación de expresiones en el IDE. [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) devuelve una estructura que puede usarse para colocar el valor de una expresión en una ventana Inspección o en la ventana variables locales.  
  
 El administrador depuración paquete o una sesión de depuración (SDM) llama [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) o [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) para obtener un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfaz que representa el resultado de la evaluación. `IDebugProperty2`tiene métodos que devuelven el nombre, el tipo y el valor de la expresión. Esta información se muestra en distintas ventanas del depurador.  
  
## <a name="using-expression-evaluation"></a>Mediante la evaluación de expresión  
 Para usar la evaluación de expresiones, debe implementar la [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) método y todos los métodos de la [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) de la interfaz, como se muestra en la tabla siguiente.  
  
|Método|Descripción|  
|------------|-----------------|  
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Evalúa una expresión de forma asincrónica.|  
|[Anulación](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Finaliza la evaluación de expresiones asincrónica.|  
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Evalúa una expresión de forma sincrónica.|  
  
 Evaluación sincrónica y asincrónica requiere la implementación de la [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) método. Evaluación de expresiones asincrónico requiere la implementación de [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md).  
  
## <a name="see-also"></a>Vea también  
 [Control de ejecución y evaluación de estado](../../extensibility/debugger/execution-control-and-state-evaluation.md)