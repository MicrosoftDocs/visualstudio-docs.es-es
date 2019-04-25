---
title: Arquitectura del evaluador de expresiones | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- architecture, expression evaluators
- expression evaluators, architecture
- debugging [Debugging SDK], expression evaluators
ms.assetid: aad7c4c6-1dc1-4d32-b975-f1fdf76bdeda
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e217b297dce18f4bca7dd5606a4ccf13240d9433
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58998685"
---
# <a name="expression-evaluator-architecture"></a>Arquitectura del evaluador de expresiones
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión del evaluador de expresiones Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Integración de un lenguaje propio en el paquete de depuración de Visual Studio significa implementar las interfaces de evaluador (EE) expresión requerido y llamar a las interfaces de enlazador y el proveedor de símbolos de tiempo de ejecución de lenguaje común (SP). Los objetos SP y el enlazador, junto con la dirección actual de ejecución, son el contexto en el que se evalúan las expresiones. La información que estas interfaces se generan y utilizan representa los conceptos clave de la arquitectura de un EE.  
  
## <a name="overview"></a>Información general  
  
### <a name="parsing-the-expression"></a>Analizar la expresión  
 Cuando se depura un programa, las expresiones se evalúan para una serie de motivos, pero siempre cuando se ha detenido el programa que se está depurando en un punto de interrupción (el usuario colocado un punto de interrupción o uno causado por una excepción). Es en este momento cuando Visual Studio obtiene un marco de pila, tal como está representada por la [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) interfaz desde el motor de depuración (DE). Visual Studio, a continuación, llama [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) para obtener el [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaz. Esta interfaz representa un contexto en el que se pueden evaluar expresiones; [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) es el punto de entrada para el proceso de evaluación. Hasta este punto, todas las interfaces se implementan mediante la DE.  
  
 Cuando `IDebugExpressionContext2::ParseText` es llama, la DE crea una instancia de lo EE asociado con el idioma del archivo de origen donde se produjo el punto de interrupción (la DE también crea una instancia de la SH en este momento). EE está representado por la [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md) interfaz. A continuación, llama a la DE [analizar](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) para convertir la expresión (en formato de texto) en una expresión analizada, está listo para su evaluación. Esta expresión analizada se representa mediante el [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) interfaz. Tenga en cuenta que la expresión se analizó normalmente y no se evalúan en este momento.  
  
 La DE crea un objeto que implementa el [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfaz pone el `IDebugParsedExpression` objeto en el `IDebugExpression2` objeto y devuelve el `IDebugExpression2` objeto desde `IDebugExpressionContext2::ParseText`.  
  
### <a name="evaluating-the-expression"></a>Evaluar la expresión  
 Visual Studio llama a [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) para evaluar la expresión analizada. Llame ambos métodos [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) (`IDebugExpression2::EvaluateSync` llama al método inmediatamente, mientras `IDebugExpression2::EvaluateAsync` llama al método a través de un subproceso en segundo plano) para evaluar la expresión analizada y devolver un [ IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfaz que representa el valor y tipo de la expresión analizada. `IDebugParsedExpression::EvaluateSync` usa el SH, la dirección y el enlazador proporcionado para convertir la expresión analizada en un valor real, representado por la `IDebugProperty2` interfaz.  
  
### <a name="for-example"></a>Por ejemplo  
 Después de que se alcance un punto de interrupción en un programa en ejecución, el usuario decide ver una variable en el **Inspección rápida** cuadro de diálogo. Este cuadro de diálogo muestra el nombre de variable, su valor y su tipo. El usuario normalmente puede cambiar el valor.  
  
 Cuando el **Inspección rápida** se muestra el cuadro de diálogo, el nombre de la variable que se está examinando se envía como texto para [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Esto devuelve un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) objeto que representa la expresión analizada, en este caso, la variable. [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) , a continuación, se llama para producir una `IDebugProperty2` objeto que representa el valor de la variable y tipo, así como su nombre. Es la información que se muestra.  
  
 Si el usuario cambia el valor de la variable, [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) se denomina con el nuevo valor, que cambia el valor de la variable en la memoria, por lo que se usará cuando el programa reanuda la ejecución.  
  
 Consulte [Mostrar variables locales](../../extensibility/debugger/displaying-locals.md) para obtener más detalles sobre este proceso de mostrar los valores de variables. Consulte [cambiar el valor de una variable Local](../../extensibility/debugger/changing-the-value-of-a-local.md) para obtener más detalles sobre cómo se cambia el valor de una variable.  
  
## <a name="in-this-section"></a>En esta sección  
 [Contexto de evaluación](../../extensibility/debugger/evaluation-context.md)  
 Proporciona los argumentos que se pasan cuando llama a la DE lo EE.  
  
 [Interfaces de evaluador de expresión de claves](../../extensibility/debugger/key-expression-evaluator-interfaces.md)  
 Describe las interfaces fundamentales necesarios al escribir un EE, junto con el contexto de evaluación.  
  
## <a name="see-also"></a>Vea también  
 [Escribir un evaluador de expresiones CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Visualización de variables locales](../../extensibility/debugger/displaying-locals.md)   
 [Cambio del valor de una variable local](../../extensibility/debugger/changing-the-value-of-a-local.md)
