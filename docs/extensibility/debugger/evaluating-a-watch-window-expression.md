---
title: "Evaluar una expresi&#243;n de la ventana Inspecci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Expresiones de la ventana de inspección"
  - "Ventana Inspección, expresiones"
  - "evaluación de expresiones, expresiones de la ventana de inspección"
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Evaluar una expresi&#243;n de la ventana Inspecci&#243;n
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está obsoleta. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [ejemplo de evaluador de expresiones administrado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Cuando la ejecución se detiene, Visual Studio llama el motor de depuración \(DE\) para determinar el valor actual de cada expresión en su lista de seguimiento. La DE evalúa cada expresión mediante un evaluador de expresiones \(EE\) y Visual Studio muestra su valor en el **inspección** ventana.  
  
 Presentamos una visión general de cómo se evalúa una expresión de inspección de la lista:  
  
1.  Visual Studio llama a la DE [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) para obtener el contexto de una expresión que se puede utilizar para evaluar expresiones.  
  
2.  Para cada expresión en la lista de observación, Visual Studio llama a [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) para convertir el texto de la expresión en una expresión analizada.  
  
3.  `IDebugExpressionContext2::ParseText` llamadas [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) para hacer el trabajo real de analizar el texto y generar un [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) objeto.  
  
4.  `IDebugExpressionContext2::ParseText` crea un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) objeto y coloca la `IDebugParsedExpression` objeto en él. Este se`DebugExpression2` a continuación, se devuelve el objeto a Visual Studio.  
  
5.  Llamadas visuales Studio [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) para evaluar la expresión analizada.  
  
6.  `IDebugExpression2::EvaluateSync` pasa la llamada a [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) para realizar la evaluación real y producir un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objeto devuelto a Visual Studio.  
  
7.  Llamadas visuales Studio [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) para obtener el valor de la expresión que se muestra a continuación, en la lista de observación.  
  
## Analizar y evaluar  
 Puesto que al analizar una expresión compleja puede tardar mucho más que la evaluación, el proceso de evaluar una expresión se divide en dos pasos: 1\) analizar la expresión y \(2\) evalúa la expresión analizada. De este modo, la evaluación puede producirse muchas veces, pero la expresión debe analizarse una sola vez. Devuelve la expresión analizada intermedia EE en un [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) objeto que a su vez se encapsula y devueltos por la DE como un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) objeto. La `IDebugExpression` objeto difiere la evaluación todas a la `IDebugParsedExpression` objeto.  
  
> [!NOTE]
>  No es necesario un EE adherirse a este proceso de dos pasos, aunque Visual Studio supone esto; puede analizar y evaluar en el mismo paso EE cuando [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) se llama \(es cómo funciona el ejemplo MyCEE, por ejemplo\). Si su lenguaje puede formar expresiones complejas, puede separar la fase de análisis del paso de la evaluación. Esto puede aumentar el rendimiento en el depurador de Visual Studio cuando muchas expresiones de inspección se van a mostrar.  
  
## En esta sección  
 [Ejemplo de implementación de evaluación de expresiones](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)  
 Utiliza el ejemplo MyCEE paso a paso a través del proceso de evaluación de expresión.  
  
 [Evaluar una expresión de inspección](../../extensibility/debugger/evaluating-a-watch-expression.md)  
 Explica lo que sucede después de un análisis de la expresión correcta.  
  
## Secciones relacionadas  
 [Contexto de evaluación](../../extensibility/debugger/evaluation-context.md)  
 Proporciona los argumentos que se pasan cuando el motor de depuración \(DE\) llama el evaluador de expresiones \(EE\).  
  
## Vea también  
 [Escribir un evaluador de expresiones de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)