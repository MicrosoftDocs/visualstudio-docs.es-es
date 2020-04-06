---
title: Evaluación de expresiones (SDK de depuración de Visual Studio) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e41179fd530818f5ac59aa54420ede1b4eafa1ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738715"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>Evaluación de expresiones (SDK de depuración de Visual Studio)
Durante el modo de interrupción, el IDE debe evaluar expresiones simples que impliquen varias variables de programa. Para realizar su evaluación, el motor de depuración (DE) debe analizar y evaluar una expresión que se ha especificado en una de las ventanas del IDE.

 Las expresiones se crean con el [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) método y representado por el resultante [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfaz.

 El **IDebugExpression2** interfaz se implementa mediante el DE y llama a su **EvalAsync** método para devolver un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfaz al IDE, con el fin de mostrar los resultados de la evaluación de expresión en el IDE. [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) devuelve una estructura que se usa para colocar el valor de una expresión en un **inspección** ventana o en el **locales** ventana.

 El paquete de depuración o el administrador de depuración de sesión (SDM) llama a [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) o [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) para obtener una interfaz [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) que representa el resultado de la evaluación. `IDebugProperty2`tiene métodos que devuelven el nombre, el tipo y el valor de la expresión. Esta información aparece en varias ventanas del depurador.

## <a name="using-expression-evaluation"></a>Uso de la evaluación de expresiones
 Para usar la evaluación de expresiones, debe implementar el [método IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) y todos los métodos de la interfaz [IDebugExpression2,](../../extensibility/debugger/reference/idebugexpression2.md) como se muestra en la tabla siguiente.

|Método|Descripción|
|------------|-----------------|
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Evalúa una expresión de forma asincrónica.|
|[Aborta](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Finaliza la evaluación de expresiones asincrónicas.|
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Evalúa una expresión de forma sincrónica.|

 La evaluación sincrónica y asincrónica requiere implementar el [método IDebugProperty2::GetPropertyInfo.](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) La evaluación de expresiones asincrónicas requiere la implementación de [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md).

## <a name="see-also"></a>Vea también
- [Control de ejecución y evaluación del estado](../../extensibility/debugger/execution-control-and-state-evaluation.md)
