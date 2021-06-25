---
title: Evaluación de expresiones (VISUAL STUDIO SDK de depuración) | Microsoft Docs
description: Durante el modo de interrupción, el IDE evalúa expresiones que implican variables de programa. Obtenga información sobre cómo el motor de depuración analiza y evalúa una expresión.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cf213c30ef26490b44579d83c68b2640360584a7
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904518"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>Evaluación de expresiones (Visual Studio SDK de depuración)
Durante el modo de interrupción, el IDE debe evaluar expresiones simples que impliquen varias variables de programa. Para realizar su evaluación, el motor de depuración (DE) debe analizar y evaluar una expresión especificada en una de las ventanas del IDE.

 Las expresiones se crean con el [método IDebugExpressionContext2::P arseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) y se representan mediante la [interfaz IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) resultante.

 El DE implementa la interfaz **IDebugExpression2** y llama a su método **EvalAsync** para devolver una interfaz [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) al IDE, con el fin de mostrar los resultados de la evaluación de expresiones en el IDE. [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) devuelve una estructura que se usa para  colocar el valor de una expresión en una ventana Watch o en la **ventana Locals.**

 El paquete de depuración o el administrador de depuración de sesión (SDM) llama a [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) o [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) para obtener una [interfaz IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) que representa el resultado de la evaluación. `IDebugProperty2` tiene métodos que devuelven el nombre, el tipo y el valor de la expresión. Esta información aparece en varias ventanas del depurador.

## <a name="using-expression-evaluation"></a>Uso de la evaluación de expresiones
 Para usar la evaluación de expresiones, debe implementar el método [IDebugExpressionContext2::P arseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) y todos los métodos de la interfaz [IDebugExpression2,](../../extensibility/debugger/reference/idebugexpression2.md) como se muestra en la tabla siguiente.

|Método|Descripción|
|------------|-----------------|
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Evalúa una expresión de forma asincrónica.|
|[Aborta](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Finaliza la evaluación de expresiones asincrónicas.|
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Evalúa una expresión de forma sincrónica.|

 La evaluación sincrónica y asincrónica requiere implementar [el método IDebugProperty2::GetPropertyInfo.](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) La evaluación de expresiones asincrónicas requiere la implementación [de IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md).

## <a name="see-also"></a>Consulta también
- [Control de ejecución y evaluación de estado](../../extensibility/debugger/execution-control-and-state-evaluation.md)
