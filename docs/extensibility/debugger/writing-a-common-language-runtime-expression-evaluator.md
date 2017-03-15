---
title: "Escribir un evaluador de expresiones de Common Language Runtime | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "evaluadores de expresión, tutorial"
  - "evaluación de expresiones, ejemplos"
  - "tutorial de evaluadores de expresión [SDK de depuración], depuración"
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# Escribir un evaluador de expresiones de Common Language Runtime
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está obsoleta. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [ejemplo de evaluador de expresiones administrado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 El evaluador de expresiones \(EE\) es la parte de un motor de depuración \(DE\) que controla la sintaxis y semántica del lenguaje de programación que genera el código que se está depurando. Las expresiones deben evaluarse en el contexto de un lenguaje de programación. Por ejemplo, en algunos idiomas, la expresión "A \+ B" significa "la suma de A y B." En otros lenguajes, la misma expresión podría significar "A o b". Por lo tanto, otro EE debe escribirse para cada lenguaje de programación que genera el código de objeto que se desea depurar en el IDE de Visual Studio.  
  
 Algunos aspectos del paquete de depuración de Visual Studio deben interpretar el código en el contexto del lenguaje de programación. Por ejemplo, cuando la ejecución se detiene en un punto de interrupción, las expresiones que el usuario ha escrito en un **inspección** ventana debe evaluar y se muestra. Además, el usuario puede cambiar el valor de una variable local, escriba una expresión en un **inspección** ventana o en el **inmediato** ventana.  
  
## En esta sección  
 [Common Language Runtime y la evaluación de expresiones](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md)  
 Explica que al lenguaje de programación patentado que integra en el IDE de Visual Studio, escribir un EE capaz de evaluación de expresiones dentro del contexto del lenguaje propietario permite compilar en un lenguaje intermedio de Microsoft \(MSIL\) sin necesidad de escribir un motor de depuración.  
  
 [Arquitectura del evaluador de expresiones](../../extensibility/debugger/expression-evaluator-architecture.md)  
 Describe cómo implementar las interfaces necesarias de EE y llamar al proveedor de símbolos en tiempo de ejecución de common language \(SP\) y las interfaces de cuaderno.  
  
 [Registrar un evaluador de expresiones](../../extensibility/debugger/registering-an-expression-evaluator.md)  
 Notas de lo EE debe registrarse como un generador de clases con el common language runtime y los entornos de tiempo de ejecución de Visual Studio.  
  
 [Implementar un evaluador de expresiones](../../extensibility/debugger/implementing-an-expression-evaluator.md)  
 Describe cómo el proceso de evaluar una expresión incluye el motor de depuración \(DE\), el proveedor de símbolos \(SP\), el objeto de enlazador y el evaluador de expresiones \(EE\).  
  
 [Mostrar variables locales](../../extensibility/debugger/displaying-locals.md)  
 Describe cómo, cuando se detiene la ejecución, el paquete de depuración llama a la DE para obtener una lista de argumentos y variables locales.  
  
 [Evaluar una expresión de la ventana Inspección](../../extensibility/debugger/evaluating-a-watch-window-expression.md)  
 Documenta cómo el paquete de depuración de Visual Studio llama a la DE para determinar el valor actual de cada expresión en su lista de seguimiento.  
  
 [Cambiar el valor de una variable Local](../../extensibility/debugger/changing-the-value-of-a-local.md)  
 Explica que, para cambiar el valor de una variable local, cada línea de la ventana variables locales tiene asociado un objeto que proporciona el nombre, el tipo y el valor actual de una variable local.  
  
 [Implementación de tipo visualizadores y visores personalizados](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md)  
 Explica la interfaz que debe ser implementada por los componentes que admiten los visualizadores de tipo y visores personalizados.  
  
## Vea también  
 [Extensibilidad del depurador de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)