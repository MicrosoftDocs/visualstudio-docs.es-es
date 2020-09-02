---
title: Evaluación de expresiones (SDK de depuración de Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0f2a84f01168dd01921d933a80fe052c1a6c6447
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62562216"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>Evaluación de expresiones (SDK de depuración de Visual Studio)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Durante el modo de interrupción, el IDE debe ser capaz de evaluar expresiones simples que afecten a varias variables del programa. Para ello, el motor de depuración (DE) debe ser capaz de analizar y evaluar una expresión que se especifica en una de las ventanas del IDE.  
  
 Las expresiones se crean mediante el método [IDebugExpressionContext2::P arsetext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) y se representan mediante la interfaz [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) resultante.  
  
 La interfaz **IDebugExpression2** se implementa mediante el método de y llama a su método **EvalAsync** para devolver una interfaz [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) al IDE, con el fin de mostrar los resultados de la evaluación de la expresión en el IDE. [IDebugProperty2:: GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) devuelve una estructura que se puede usar para colocar el valor de una expresión en un ventana Inspección o en la ventana variables locales.  
  
 El paquete de depuración o el administrador de depuración de sesión (SDM) llama a [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) o [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) para obtener una interfaz [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) que representa el resultado de la evaluación. `IDebugProperty2` tiene métodos que devuelven el nombre, el tipo y el valor de la expresión. Esta información se muestra en varias ventanas del depurador.  
  
## <a name="using-expression-evaluation"></a>Usar la evaluación de expresiones  
 Para usar la evaluación de expresiones, debe implementar el método [IDebugExpressionContext2::P arsetext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) y todos los métodos de la interfaz [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) , como se muestra en la tabla siguiente.  
  
|Método|Descripción|  
|------------|-----------------|  
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Evalúa una expresión de forma asincrónica.|  
|[Anulación](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Finaliza la evaluación de expresiones asincrónicas.|  
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Evalúa una expresión sincrónicamente.|  
  
 La evaluación sincrónica y asincrónica requiere la implementación del método [IDebugProperty2:: GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) . La evaluación de expresiones asincrónicas requiere la implementación de [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md).  
  
## <a name="see-also"></a>Consulte también  
 [Control de ejecución y evaluación de estado](../../extensibility/debugger/execution-control-and-state-evaluation.md)
