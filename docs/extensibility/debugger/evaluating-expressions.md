---
title: Evaluar expresiones | Microsoft Docs
description: Obtenga información sobre la evaluación de expresiones, que se crean a partir de cadenas que pasan de las ventanas automático, inspección, inspección rápida o inmediata.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: b43fc91de129407f2fd01e12951cffee4028186f
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914600"
---
# <a name="evaluate-expressions"></a>Evaluar expresiones
Las expresiones se crean a partir de las cadenas que se pasan de las ventanas **automático**, **inspección**, **Inspección rápida** o **inmediata** . Cuando se evalúa una expresión, genera una cadena imprimible que contiene el nombre y el tipo de variable o argumento y su valor. Esta cadena se muestra en la ventana del IDE correspondiente.

## <a name="implementation"></a>Implementación
 Las expresiones se evalúan cuando un programa se detiene en un punto de interrupción. La propia expresión se representa mediante una interfaz [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) , que representa una expresión analizada que está lista para el enlace y la evaluación dentro del contexto de evaluación de expresión determinado. El marco de pila determina el contexto de evaluación de expresiones, que el motor DE depuración (DE) proporciona mediante la implementación de la interfaz [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) .

 Dada una cadena de usuario y una interfaz [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) , un motor de depuración (de) puede obtener una interfaz [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) pasando la cadena de usuario al método [IDebugExpressionContext2::P arsetext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) . La interfaz IDebugExpression2 que se devuelve contiene la expresión analizada lista para su evaluación.

 Con la `IDebugExpression2` interfaz, el de puede obtener el valor de la expresión a través de la evaluación de expresiones sincrónicas o asincrónicas mediante [IDebugExpression2:: EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md). Este valor, junto con el nombre y el tipo de la variable o argumento, se envía al IDE para su presentación. El valor, el nombre y el tipo se representan mediante una interfaz [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) .

 Para habilitar la evaluación DE expresiones, un DE debe implementar las interfaces [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) y [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) . La evaluación sincrónica y asincrónica requiere la implementación del método [IDebugProperty2:: GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) .

## <a name="see-also"></a>Consulte también
- [Marcos de pila](../../extensibility/debugger/stack-frames.md)
- [Contexto de evaluación de expresiones](../../extensibility/debugger/expression-evaluation-context.md)
- [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)
