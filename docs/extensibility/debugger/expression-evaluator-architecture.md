---
title: "Arquitectura del evaluador de expresiones | Microsoft Docs"
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
  - "arquitectura de evaluadores de expresión"
  - "evaluadores de expresión, arquitectura"
  - "depurar [SDK de depuración], evaluadores de expresión"
ms.assetid: aad7c4c6-1dc1-4d32-b975-f1fdf76bdeda
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Arquitectura del evaluador de expresiones
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está obsoleta. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [ejemplo de evaluador de expresiones administrado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Integrar el paquete de depuración de Visual Studio en un lenguaje patentado significa implementar las interfaces de evaluador \(EE\) expresión requerido y llamar a las interfaces de cuaderno y el proveedor de símbolos de tiempo de ejecución de lenguaje común \(SP\). Los objetos de SP y cuaderno, junto con la dirección actual de ejecución, son el contexto en que se evalúan las expresiones. La información que estas interfaces producen y consumen representa los conceptos clave en la arquitectura de un EE.  
  
## Información general  
  
### Analizar la expresión  
 Cuando se depura un programa, las expresiones se evalúan por diferentes motivos, pero siempre cuando se ha detenido el programa que se está depurando en un punto de interrupción \(un punto de interrupción colocado por el usuario o uno causado por una excepción\). Es en este momento cuando Visual Studio obtiene un marco de pila representado por la [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) interfaz desde el motor de depuración \(DE\). Visual Studio, a continuación, llama a [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) para obtener el [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaz. Esta interfaz representa un contexto en el que se pueden evaluar expresiones; [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) es el punto de entrada para el proceso de evaluación. Hasta este punto, la DE implementa todas las interfaces.  
  
 Cuando `IDebugExpressionContext2::ParseText` es la DE llama, crea instancias EE asociado con el idioma del archivo de origen donde se produjo el punto de interrupción \(la DE también crea una instancia de la SH en este momento\). EE está representado por la [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md) interfaz. A continuación, llama a la DE [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) para convertir la expresión \(en formato de texto\) en una expresión analizada, está listo para su evaluación. Esta expresión analizada se representa mediante el [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) interfaz. Tenga en cuenta que la expresión se analizan normalmente y no se evalúa en este momento.  
  
 El DE crea un objeto que implementa el [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfaz coloca la `IDebugParsedExpression` objeto en el `IDebugExpression2` objeto y devuelve el `IDebugExpression2` objeto de `IDebugExpressionContext2::ParseText`.  
  
### Evaluar la expresión  
 Visual Studio llama a [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) para evaluar la expresión analizada. Llame ambos métodos [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) \(`IDebugExpression2::EvaluateSync` llama al método inmediatamente, mientras que `IDebugExpression2::EvaluateAsync` llama al método a través de un subproceso en segundo plano\) para evaluar la expresión analizada y devolver un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfaz que representa el valor y el tipo de la expresión analizada.`IDebugParsedExpression::EvaluateSync` El SH, la dirección y el enlazador proporcionado se utiliza para convertir la expresión analizada en un valor real, representado por la `IDebugProperty2` interfaz.  
  
### Por ejemplo  
 Después de un punto de interrupción en un programa en ejecución, el usuario decide ver una variable en el **Inspección rápida** cuadro de diálogo. Este cuadro de diálogo muestra el nombre de la variable, su valor y su tipo. El usuario normalmente puede cambiar el valor.  
  
 Cuando el **Inspección rápida** se muestra el cuadro de diálogo, el nombre de la variable que se está examinando se envía como texto en [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Esto devuelve un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) objeto que representa la expresión analizada, en este caso, la variable.[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) a continuación, se llama para producir una `IDebugProperty2` objeto que representa el valor de la variable y el tipo, así como su nombre. Es la información que se muestra.  
  
 Si el usuario cambia el valor de la variable, [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) se llama con el nuevo valor, que cambia el valor de la variable en la memoria de modo que se usará cuando se reanuda el programa ejecuta.  
  
 Consulte [Mostrar variables locales](../../extensibility/debugger/displaying-locals.md) para obtener más información acerca de este proceso de presentación de los valores de variables. Consulte [Cambiar el valor de una variable Local](../../extensibility/debugger/changing-the-value-of-a-local.md) para obtener más detalles sobre cómo se cambia el valor de la variable.  
  
## En esta sección  
 [Contexto de evaluación](../../extensibility/debugger/evaluation-context.md)  
 Proporciona los argumentos que se pasan cuando llama a la DE lo EE.  
  
 [Interfaces de evaluador de expresión de clave](../../extensibility/debugger/key-expression-evaluator-interfaces.md)  
 Describe las interfaces fundamentales necesarios al escribir un EE, junto con el contexto de evaluación.  
  
## Vea también  
 [Escribir un evaluador de expresiones de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Mostrar variables locales](../../extensibility/debugger/displaying-locals.md)   
 [Cambiar el valor de una variable Local](../../extensibility/debugger/changing-the-value-of-a-local.md)