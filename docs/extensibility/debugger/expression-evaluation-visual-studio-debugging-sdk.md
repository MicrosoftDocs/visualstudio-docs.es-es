---
title: Evaluación de expresiones (SDK de depuración de Visual Studio) | Microsoft Docs
description: Durante el modo de interrupción, el IDE evalúa las expresiones que implican variables de programa. Obtenga información sobre cómo el motor de depuración analiza y evalúa una expresión.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 8c398d9eb79a6b5fcd1a6851596ab8913faf32fa
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560894"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>Evaluación de expresiones (SDK de depuración de Visual Studio)
Durante el modo de interrupción, el IDE debe evaluar expresiones simples que impliquen varias variables de programa. Para realizar su evaluación, el motor de depuración (DE) debe analizar y evaluar una expresión que se especifica en una de las ventanas del IDE.

 Las expresiones se crean con el método [IDebugExpressionContext2::P arsetext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) y se representan mediante la interfaz [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) resultante.

 La interfaz **IDebugExpression2** se implementa mediante el método de y llama a su método **EvalAsync** para devolver una interfaz [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) al IDE, con el fin de mostrar los resultados de la evaluación de la expresión en el IDE. [IDebugProperty2:: GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) devuelve una estructura que se usa para colocar el valor de una expresión en una ventana **inspección** o en la ventana **variables locales** .

 El paquete de depuración o el administrador de depuración de sesión (SDM) llama a [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) o [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) para obtener una interfaz [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) que representa el resultado de la evaluación. `IDebugProperty2` tiene métodos que devuelven el nombre, el tipo y el valor de la expresión. Esta información aparece en varias ventanas del depurador.

## <a name="using-expression-evaluation"></a>Usar la evaluación de expresiones
 Para usar la evaluación de expresiones, debe implementar el método [IDebugExpressionContext2::P arsetext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) y todos los métodos de la interfaz [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) , como se muestra en la tabla siguiente.

|Método|Descripción|
|------------|-----------------|
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Evalúa una expresión de forma asincrónica.|
|[Anulación](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Finaliza la evaluación de expresiones asincrónicas.|
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Evalúa una expresión sincrónicamente.|

 La evaluación sincrónica y asincrónica requiere la implementación del método [IDebugProperty2:: GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) . La evaluación de expresiones asincrónicas requiere la implementación de [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md).

## <a name="see-also"></a>Vea también
- [Control de ejecución y evaluación del estado](../../extensibility/debugger/execution-control-and-state-evaluation.md)
