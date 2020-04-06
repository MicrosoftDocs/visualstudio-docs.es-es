---
title: Evaluación de expresiones ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK], evaluating
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 18e342704cbb4abd7de9667576ce331ef8fbf60a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738834"
---
# <a name="evaluate-expressions"></a>Evaluar expresiones
Las expresiones se crean a partir de cadenas que se pasan desde las **ventanas Autos**, **Watch**, **QuickWatch**o **Immediate.** Cuando se evalúa una expresión, genera una cadena imprimible que contiene el nombre y el tipo de variable o argumento y su valor. Esta cadena se muestra en la ventana IDE correspondiente.

## <a name="implementation"></a>Implementación
 Las expresiones se evalúan cuando un programa se ha detenido en un punto de interrupción. La expresión en sí se representa mediante un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfaz, que representa una expresión analizada que está lista para el enlace y la evaluación dentro del contexto de evaluación de expresión dado. El marco de pila determina el contexto de evaluación de expresiones, que el motor de depuración (DE) proporciona mediante la implementación de la [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaz.

 Dado una cadena de usuario y un [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaz, un motor de depuración (DE) puede obtener un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfaz pasando la cadena de usuario a la [IDebugExpressionContext2:arse :PText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) método. El IDebugExpression2 interfaz que se devuelve contiene la expresión analizada lista para la evaluación.

 Con `IDebugExpression2` la interfaz, la DE puede obtener el valor de la expresión mediante la evaluación de expresiones sincrónicas o asincrónicas, mediante [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md). Este valor, junto con el nombre y el tipo de la variable o argumento, se envía al IDE para su presentación. El valor, el nombre y el tipo se representan mediante una interfaz [IDebugProperty2.](../../extensibility/debugger/reference/idebugproperty2.md)

 Para habilitar la evaluación de expresiones, un DE debe implementar el [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) y [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaces. La evaluación sincrónica y asincrónica requiere la implementación de la [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) método.

## <a name="see-also"></a>Vea también
- [Marcos de pila](../../extensibility/debugger/stack-frames.md)
- [Contexto de evaluación de expresiones](../../extensibility/debugger/expression-evaluation-context.md)
- [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)
