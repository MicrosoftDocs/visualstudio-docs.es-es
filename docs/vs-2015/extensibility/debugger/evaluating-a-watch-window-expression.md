---
title: Evaluar una expresión de la ventana Inspección | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Watch window expressions
- Watch window, expressions
- expression evaluation, Watch window expressions
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f13573cfecbd81f36e3b77e9b23beeaa558c08dc
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444787"
---
# <a name="evaluating-a-watch-window-expression"></a>Evaluación de una expresión de la ventana Inspección
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión del evaluador de expresiones Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Cuando la ejecución se detiene, Visual Studio llama al motor de depuración (DE) para determinar el valor actual de cada expresión en su lista de supervisión. La DE evalúa cada expresión utilizando un evaluador de expresiones (EE) y Visual Studio muestra su valor en el **inspección** ventana.  
  
 Presentamos una visión general de cómo se evalúa una expresión de la lista de observación:  
  
1. Visual Studio llama a la DE [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) para obtener el contexto de una expresión que se puede usar para evaluar expresiones.  
  
2. Para cada expresión en la lista de observación, Visual Studio llama [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) para convertir el texto de expresión en una expresión analizada.  
  
3. `IDebugExpressionContext2::ParseText` las llamadas [analizar](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) para realizar el trabajo real de analizar el texto y generan un [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) objeto.  
  
4. `IDebugExpressionContext2::ParseText` crea un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) objeto y lo sustituye por la `IDebugParsedExpression` objeto en él. Este se`DebugExpression2` , a continuación, se devuelve el objeto Visual Studio.  
  
5. Llamadas visuales Studio [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) para evaluar la expresión analizada.  
  
6. `IDebugExpression2::EvaluateSync` pasa la llamada a [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) para realizar la evaluación real y generar un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objeto devuelto a Visual Studio.  
  
7. Llamadas visuales Studio [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) para obtener el valor de la expresión que se muestra a continuación, en la lista de observación.  
  
## <a name="parse-then-evaluate"></a>Analizar, a continuación, evaluar  
 Puesto que al analizar una expresión compleja puede durar bastante más que la evaluación, el proceso de evaluar una expresión se divide en dos pasos: la expresión de análisis (1) y 2) evalúa la expresión analizada. De este modo, la evaluación puede producirse muchas veces, pero la expresión debe analizarse en una sola vez. Se devuelve la expresión analizada intermedia de lo EE en un [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) objeto que a su vez se encapsula y devueltos por la DE como un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) objeto. El `IDebugExpression` objeto aplaza la evaluación de todas las `IDebugParsedExpression` objeto.  
  
> [!NOTE]
> No es necesario para un EE adherirse a este proceso en dos pasos, aunque Visual Studio se da por supuesto esto; puede analizar y evaluar en el mismo paso EE cuando [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) se llama (Esto es cómo funciona el ejemplo MyCEE, por ejemplo). Si su lenguaje puede formar expresiones complejas, puede separar la fase de análisis desde el paso de evaluación. Esto puede aumentar el rendimiento en el depurador de Visual Studio cuando muchas expresiones de inspección se muestran.  
  
## <a name="in-this-section"></a>En esta sección  
 [Implementación de ejemplo de la evaluación de expresiones](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)  
 Usa el ejemplo MyCEE paso a paso a través del proceso de evaluación de expresiones.  
  
 [Evaluación de una expresión de inspección](../../extensibility/debugger/evaluating-a-watch-expression.md)  
 Explica lo que ocurre tras un análisis de expresión correcta.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Contexto de evaluación](../../extensibility/debugger/evaluation-context.md)  
 Proporciona los argumentos que se pasan cuando el motor de depuración (DE) llama el evaluador de expresiones (EE).  
  
## <a name="see-also"></a>Vea también  
 [Escritura de un evaluador de expresiones CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
