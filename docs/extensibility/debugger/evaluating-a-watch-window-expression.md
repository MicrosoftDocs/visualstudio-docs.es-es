---
title: Evaluación de una expresión de ventana de inspección ( Watch Window Expression) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Watch window expressions
- Watch window, expressions
- expression evaluation, Watch window expressions
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9cef2f27eec095ee7b136153ecb764feba9effbb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738837"
---
# <a name="evaluate-a-watch-window-expression"></a>Evaluar una expresión de ventana de inspección
> [!IMPORTANT]
> En Visual Studio 2015, esta forma de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, vea Evaluadores de [expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y Ejemplo de evaluador de [expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Cuando se detiene la ejecución, Visual Studio llama al motor de depuración (DE) para determinar el valor actual de cada expresión en su lista de inspección. La DE evalúa cada expresión mediante un evaluador de expresiones (EE) y Visual Studio muestra su valor en la ventana **Inspección.**

 A continuación se muestra una descripción general de cómo se evalúa una expresión de lista de inspección:

1. Visual Studio llama a [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) de la DE para obtener un contexto de expresión que se puede usar para evaluar expresiones.

2. Para cada expresión de la lista de inspección, Visual Studio llama a [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) para convertir el texto de la expresión en una expresión analizada.

3. `IDebugExpressionContext2::ParseText`llama a [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) para realizar el trabajo real de analizar el texto y generar un [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) objeto.

4. `IDebugExpressionContext2::ParseText`crea un [objeto IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) `IDebugParsedExpression` y coloca el objeto en él. Este`DebugExpression2` objeto I, a continuación, se devuelve a Visual Studio.

5. Visual Studio llama a [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) para evaluar la expresión analizada.

6. `IDebugExpression2::EvaluateSync`pasa la llamada a [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) para realizar la evaluación real y generar un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objeto que se devuelve a Visual Studio.

7. Visual Studio llama a [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) para obtener el valor de la expresión que, a continuación, se muestra en la lista de inspección.

## <a name="parse-then-evaluate"></a>Analizar y luego evaluar
 Dado que el análisis de una expresión compleja puede tardar mucho más que evaluarla, el proceso de evaluación de una expresión se divide en dos pasos: 1) analizar la expresión y 2) evaluar la expresión analizada. De esta manera, la evaluación puede producirse muchas veces, pero la expresión debe analizarse una sola vez. La expresión analizada intermedia se devuelve desde el EE en un [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) objeto que a su vez se encapsula y se devuelve desde el DE como un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) objeto. El `IDebugExpression` objeto aplaza toda `IDebugParsedExpression` la evaluación al objeto.

> [!NOTE]
> No es necesario que un EE se adhiera a este proceso de dos pasos aunque Visual Studio asume esto; EE puede analizar y evaluar en el mismo paso cuando se llama a [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) (así es como funciona el ejemplo MyCEE, por ejemplo). Si su lenguaje puede formar expresiones complejas, es posible que desee separar el paso de análisis del paso de evaluación. Esto puede aumentar el rendimiento en el depurador de Visual Studio cuando se muestran muchas expresiones de inspección.

## <a name="in-this-section"></a>En esta sección
 [Ejemplo de implementación de la evaluación de expresiones](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md) Utiliza el ejemplo MyCEE para recorrer paso a paso el proceso de evaluación de expresiones.

 [Evaluación de una expresión de reloj](../../extensibility/debugger/evaluating-a-watch-expression.md) Explica lo que sucede después de un análisis de expresión correcto.

## <a name="related-sections"></a>Secciones relacionadas
 [Contexto de evaluación](../../extensibility/debugger/evaluation-context.md) Proporciona los argumentos que se pasan cuando el motor de depuración (DE) llama al evaluador de expresiones (EE).

## <a name="see-also"></a>Vea también
 [Escribir un evaluador de expresiones CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
