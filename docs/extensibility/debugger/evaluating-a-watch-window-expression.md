---
title: "Evaluar una expresión de la ventana de inspección | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Watch window expressions
- Watch window, expressions
- expression evaluation, Watch window expressions
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 03a74bf73f457009a6f17f8e7bdda8e4e7b9e35f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="evaluating-a-watch-window-expression"></a>Evaluar una expresión de la ventana Inspección
> [!IMPORTANT]
>  Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información acerca de cómo implementar los evaluadores de expresión de CLR, vea [evaluadores de expresión de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión evaluador Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Cuando la ejecución se detiene, Visual Studio llama el motor de depuración (Alemania) para determinar el valor actual de cada expresión en su lista de supervisión. El Alemania evalúa cada expresión mediante un evaluador de expresiones (EE) y Visual Studio muestra su valor en el **inspección** ventana.  
  
 Aquí indicamos una introducción de cómo se evalúa una expresión de inspección de la lista:  
  
1.  Visual Studio llama a la DE [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) para obtener el contexto de una expresión que se puede utilizar para evaluar expresiones.  
  
2.  Para cada expresión en la lista de inspección, Visual Studio llama a [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) para convertir el texto de la expresión en una expresión analizada.  
  
3.  `IDebugExpressionContext2::ParseText`llamadas [analizar](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) para hacer el trabajo real de analizar el texto y producen una [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) objeto.  
  
4.  `IDebugExpressionContext2::ParseText`crea un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) objeto y coloca la `IDebugParsedExpression` objeto en él. Este se`DebugExpression2` , a continuación, se devuelve el objeto Visual Studio.  
  
5.  Llamadas visuales Studio [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) para evaluar la expresión analizada.  
  
6.  `IDebugExpression2::EvaluateSync`pasa la llamada a [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) para realizar la evaluación real y generar un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objeto que se devuelve a Visual Studio.  
  
7.  Llamadas visuales Studio [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) para obtener el valor de la expresión que se muestra a continuación, en la lista de supervisión.  
  
## <a name="parse-then-evaluate"></a>Analizar, a continuación, evaluar  
 Puesto que analizar una expresión compleja puede tardar mucho más que la evaluación, el proceso de evaluar una expresión se divide en dos pasos: 1) analizar la expresión y (2) evalúa la expresión analizada. De esta manera, la evaluación puede aparecer muchas veces, pero la expresión se debe analizar una sola vez. Se devuelve la expresión analizada intermedia de lo EE en un [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) objeto que a su vez se encapsula y devueltos por la DE como un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) objeto. El `IDebugExpression` objeto aplaza toda la evaluación a la `IDebugParsedExpression` objeto.  
  
> [!NOTE]
>  No es necesario para un EE cumplir con este proceso de dos pasos aunque Visual Studio se da por supuesto esto. puede analizar y evaluar en el mismo paso de lo EE cuando [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) se denomina (se trata cómo funciona el ejemplo MyCEE, por ejemplo). Si su lenguaje puede formar expresiones complejas, puede que desee separar la fase de análisis en el paso de la evaluación. Esto puede aumentar el rendimiento en el depurador de Visual Studio cuando muchas expresiones de inspección se van a mostrar.  
  
## <a name="in-this-section"></a>En esta sección  
 [Implementación de ejemplo de la evaluación de expresiones](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)  
 Usa el ejemplo MyCEE paso a paso a través del proceso de evaluación de expresiones.  
  
 [Evaluación de una expresión de inspección](../../extensibility/debugger/evaluating-a-watch-expression.md)  
 Explica lo que ocurre tras un análisis de la expresión correctamente.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Contexto de evaluación](../../extensibility/debugger/evaluation-context.md)  
 Proporciona los argumentos que se pasan cuando el motor de depuración (Alemania) llama el evaluador de expresiones (EE).  
  
## <a name="see-also"></a>Vea también  
 [Escribir un evaluador de expresiones de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)