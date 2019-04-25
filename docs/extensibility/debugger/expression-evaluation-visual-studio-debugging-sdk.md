---
title: Evaluación de expresiones (SDK de depuración de Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5b100ccac042aeed3ed8211c56fc1129311d850b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56723180"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>Evaluación de expresiones (depuración de SDK de Visual Studio)
Modo de interrupción, el IDE debe evaluar las expresiones simples que implican varias variables de programa. Para llevar a cabo su evaluación, el motor de depuración (DE) debe analizar y evaluar una expresión que se escriban en una de las ventanas del IDE.

 Las expresiones se crean con el [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) método y se representan mediante resultante [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfaz.

 El **IDebugExpression2** interfaz se implementa mediante las llamadas y DE su **EvalAsync** método devuelva un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfaz para el IDE, con el fin de mostrar el resultados de la evaluación de expresión en el IDE. [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) devuelve una estructura que se utiliza para colocar el valor de una expresión en un **inspección** ventana o en el **variables locales** ventana.

 El administrador depuración paquete o una sesión de depuración (SDM) llama [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) o [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) para obtener un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfaz que representa el resultado de la evaluación. `IDebugProperty2` tiene métodos que devuelven el nombre, tipo y valor de la expresión. Esta información aparece en distintas ventanas del depurador.

## <a name="using-expression-evaluation"></a>Uso de la evaluación de expresiones
 Para usar la evaluación de expresiones, debe implementar la [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) método y todos los métodos de la [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfaz, como se muestra en la tabla siguiente.

|Método|Descripción|
|------------|-----------------|
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Evalúa una expresión de forma asincrónica.|
|[Abort](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Finaliza la evaluación de expresiones asincrónicas.|
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Evalúa una expresión de forma sincrónica.|

 Evaluación sincrónica y asincrónica necesario implementar el [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) método. Evaluación de expresiones asincrónico requiere la implementación de [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md).

## <a name="see-also"></a>Vea también
- [Evaluación de control y el estado de ejecución](../../extensibility/debugger/execution-control-and-state-evaluation.md)