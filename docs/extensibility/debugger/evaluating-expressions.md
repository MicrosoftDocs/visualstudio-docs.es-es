---
title: Evaluación de expresiones | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK], evaluating
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 39b2af1cdf299b3e3f2c714fa569fa295a4e1d4e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315425"
---
# <a name="evaluate-expressions"></a>Evaluar expresiones
Las expresiones se crean a partir de cadenas que se pasan desde el **automático**, **inspección**, **Inspección rápida**, o **inmediato** windows. Cuando se evalúa una expresión, genera una cadena imprimible que contiene el nombre y tipo de variable o argumento y su valor. Esta cadena se muestra en la ventana del IDE correspondiente.

## <a name="implementation"></a>Implementación
 Las expresiones se evalúan cuando se ha detenido un programa en un punto de interrupción. La expresión se representa mediante un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfaz, que representa una expresión analizada que está lista para enlace y evaluación dentro del contexto de evaluación de la expresión dada. El marco de pila determina el contexto de evaluación de expresión, que proporciona el motor de depuración (DE) implementando la [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaz.

 Dada una cadena de usuario y una [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaz, puede obtener un motor de depuración (DE) un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfaz, pase la cadena de usuario para el [ IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) método. La interfaz IDebugExpression2 devuelto contiene la expresión analizada lista para su evaluación.

 Con el `IDebugExpression2` interfaz, la DE puede obtener el valor de la expresión a través de la evaluación de expresiones sincrónica o asincrónica, utilizando [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md). Este valor, junto con el nombre y tipo de la variable o argumento, se envía en el IDE para su presentación. El valor, el nombre y el tipo se representan mediante un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfaz.

 Para habilitar la evaluación de expresiones, debe implementar a DE la [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) y [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaces. Evaluación sincrónica y asincrónica requiere la implementación de la [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) método.

## <a name="see-also"></a>Vea también
- [Marcos de pila](../../extensibility/debugger/stack-frames.md)
- [Contexto de evaluación de expresión](../../extensibility/debugger/expression-evaluation-context.md)
- [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)