---
title: Escribir un evaluador de expresiones de Common Language Runtime | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators, tutorial
- expression evaluation, samples
- debugging [Debugging SDK], expression evaluators tutorial
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 961a4d646a61fedda381f9451902b3bcdcc956d6
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435277"
---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>Escritura de un evaluador de expresiones de Common Language Runtime
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión del evaluador de expresiones Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 El evaluador de expresiones (EE) es la parte de un motor de depuración (DE) que controla la sintaxis y semántica del lenguaje de programación que generó el código que se está depurando. Las expresiones deben evaluarse en el contexto de un lenguaje de programación. Por ejemplo, en algunos idiomas, la expresión "A + B" significa "la suma de A y B." En otros lenguajes, la misma expresión podría significar "A o b". Por lo tanto, otro EE debe estar escrita para cada lenguaje de programación que genera el código de objeto que se desea depurar en el IDE de Visual Studio.  
  
 Algunos aspectos del paquete de depuración de Visual Studio deben interpretar el código en el contexto del lenguaje de programación. Por ejemplo, cuando la ejecución se detiene en un punto de interrupción, las expresiones que el usuario ha escrito en un **inspección** debe se evalúa y muestra la ventana. Además, el usuario puede cambiar el valor de una variable local para ello, escriba una expresión en un **inspección** ventana o en el **inmediato** ventana.  
  
## <a name="in-this-section"></a>En esta sección  
 [Common Language Runtime y la evaluación de expresiones](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md)  
 Se explica que al lenguaje de programación patentado que integra en el IDE de Visual Studio, escribir un EE capaz de evaluación de expresiones dentro del contexto del lenguaje propietario le permite compilar en un lenguaje intermedio de Microsoft (MSIL) sin necesidad de escribir un motor de depuración.  
  
 [Arquitectura del evaluador de expresiones](../../extensibility/debugger/expression-evaluator-architecture.md)  
 Describe cómo implementar las interfaces necesarias de EE y llamar al proveedor de símbolos de tiempo de ejecución de lenguaje común (SP) y las interfaces del cuaderno.  
  
 [Registro de un evaluador de expresiones](../../extensibility/debugger/registering-an-expression-evaluator.md)  
 Notas de la que el EE se debe registrar como un generador de clases con el common language runtime y el entornos en tiempo de ejecución de Visual Studio.  
  
 [Implementación de un evaluador de expresiones](../../extensibility/debugger/implementing-an-expression-evaluator.md)  
 Describe cómo el proceso de evaluar una expresión incluye en el motor de depuración (DE), el proveedor de símbolos (SP), el objeto de enlazador y el evaluador de expresiones (EE).  
  
 [Visualización de variables locales](../../extensibility/debugger/displaying-locals.md)  
 Describe cómo, cuando la ejecución se detiene, el paquete de depuración llama a la DE para obtener una lista de argumentos y variables locales.  
  
 [Evaluación de una expresión de la ventana Inspección](../../extensibility/debugger/evaluating-a-watch-window-expression.md)  
 Documenta cómo el paquete de depuración de Visual Studio llama a la DE para determinar el valor actual de cada expresión en su lista de supervisión.  
  
 [Cambio del valor de una variable local](../../extensibility/debugger/changing-the-value-of-a-local.md)  
 Explica que cambiar el valor de una variable local, cada línea de la ventana variables locales tiene asociado un objeto que proporciona el nombre, el tipo y el valor actual de una variable local.  
  
 [Implementación de visualizadores de tipo y visores personalizados](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md)  
 Explica qué interfaz debe implementarse mediante los componentes que admiten visualizadores de tipo y visores personalizados.  
  
## <a name="see-also"></a>Vea también  
 [Extensibilidad del depurador de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
