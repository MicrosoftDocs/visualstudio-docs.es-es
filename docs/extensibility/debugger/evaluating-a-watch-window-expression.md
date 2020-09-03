---
title: Evaluar una expresión de ventana de inspección | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738837"
---
# <a name="evaluate-a-watch-window-expression"></a>Evaluar una expresión de la ventana Inspección
> [!IMPORTANT]
> En Visual Studio 2015, esta manera de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, consulte [evaluadores](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) de expresiones CLR y [ejemplo de evaluador de expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Cuando la ejecución se pausa, Visual Studio llama al motor de depuración (DE) para determinar el valor actual de cada expresión en su lista de inspección. El DE evalúa cada expresión usando un evaluador de expresiones (EE) y Visual Studio muestra su valor en la ventana **inspección** .

 A continuación se muestra una visión general de cómo se evalúa una expresión de lista de inspección:

1. Visual Studio llama a [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) para obtener un contexto de expresión que se puede usar para evaluar expresiones.

2. Para cada expresión de la lista de inspección, Visual Studio llama a [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) para convertir el texto de la expresión en una expresión analizada.

3. `IDebugExpressionContext2::ParseText` llama a [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) para realizar el trabajo real de analizar el texto y generar un objeto [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) .

4. `IDebugExpressionContext2::ParseText` crea un objeto [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) y coloca el `IDebugParsedExpression` objeto en él. `DebugExpression2`A continuación, este objeto I se devuelve a Visual Studio.

5. Visual Studio llama a [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) para evaluar la expresión analizada.

6. `IDebugExpression2::EvaluateSync` pasa la llamada a [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) para realizar la evaluación real y generar un objeto [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) que se devuelve a Visual Studio.

7. Visual Studio llama a [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) para obtener el valor de la expresión que se muestra a continuación en la lista de inspección.

## <a name="parse-then-evaluate"></a>Analizar después evaluar
 Dado que el análisis de una expresión compleja puede tardar mucho más que evaluarla, el proceso de evaluación de una expresión se divide en dos pasos: 1) analizar la expresión y 2) evaluar la expresión analizada. De este modo, la evaluación puede producirse muchas veces, pero la expresión solo debe analizarse una vez. La expresión analizada intermedia se devuelve desde EE en un objeto [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) que, a su vez, se encapsula y se devuelve de de como un objeto [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) . El `IDebugExpression` objeto aplaza toda la evaluación en el `IDebugParsedExpression` objeto.

> [!NOTE]
> No es necesario que un EE se adhiere a este proceso de dos pasos, aunque Visual Studio lo asuma. EE puede analizar y evaluar en el mismo paso cuando se llama a [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) (este es el funcionamiento del ejemplo de MyCEE, por ejemplo). Si su lenguaje puede formar expresiones complejas, puede que desee separar el paso de análisis del paso de evaluación. Esto puede aumentar el rendimiento en el depurador de Visual Studio cuando se muestran muchas expresiones de inspección.

## <a name="in-this-section"></a>En esta sección
 [Implementación de ejemplo de evaluación de expresiones](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md) Usa el ejemplo MyCEE para recorrer el proceso de evaluación de expresiones.

 [Evaluación de una expresión de inspección](../../extensibility/debugger/evaluating-a-watch-expression.md) Explica lo que ocurre después de un análisis correcto de la expresión.

## <a name="related-sections"></a>Secciones relacionadas
 [Contexto de evaluación](../../extensibility/debugger/evaluation-context.md) Proporciona los argumentos que se pasan cuando el motor DE depuración (DE) llama al evaluador de expresiones (EE).

## <a name="see-also"></a>Consulte también
 [Escribir un evaluador de expresiones CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
