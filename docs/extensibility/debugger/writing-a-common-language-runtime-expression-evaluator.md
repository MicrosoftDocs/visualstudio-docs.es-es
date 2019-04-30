---
title: Escribir un evaluador de expresiones de Common Language Runtime | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators, tutorial
- expression evaluation, samples
- debugging [Debugging SDK], expression evaluators tutorial
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59c7ec2b6313ee27fc46c778f8b19e104b169273
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63421468"
---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>Escribir un evaluador de expresiones de common language runtime
> [!IMPORTANT]
> En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [ejemplo de evaluador de expresión administrado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 El evaluador de expresiones (EE) es la parte de un motor de depuración (DE) que controla la sintaxis y semántica del lenguaje de programación que generó el código que se está depurando. Las expresiones deben evaluarse en el contexto de un lenguaje de programación. Por ejemplo, en algunos idiomas, la expresión "A + B" significa "la suma de A y B." En otros lenguajes, la misma expresión podría significar "A o b". Por lo tanto, otro EE debe estar escrita para cada lenguaje de programación que genera el código de objeto que se desea depurar en el IDE de Visual Studio.

 Algunos aspectos del paquete de depuración de Visual Studio deben interpretar el código en el contexto del lenguaje de programación. Por ejemplo, cuando la ejecución se detiene en un punto de interrupción, las expresiones que el usuario ha escrito en un **inspección** debe se evalúa y muestra la ventana. El usuario puede cambiar el valor de una variable local para ello, escriba una expresión en un **inspección** ventana o en el **inmediato** ventana.

## <a name="in-this-section"></a>En esta sección
 [Evaluación de tiempo de ejecución y la expresión de lenguaje común](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md) explica que, cuando se va a integrar propietaria lenguaje de programación en el IDE de Visual Studio, escribir un EE capaz de evaluación de expresiones dentro del contexto del lenguaje propietario permite compilar en un lenguaje intermedio de Microsoft (MSIL) sin necesidad de escribir un motor de depuración.

 [Arquitectura del evaluador de expresiones](../../extensibility/debugger/expression-evaluator-architecture.md) se explica cómo implementar las interfaces necesarias de EE y llamar al proveedor de símbolos de tiempo de ejecución de lenguaje común (SP) y las interfaces del cuaderno.

 [Registrar un evaluador de expresiones](../../extensibility/debugger/registering-an-expression-evaluator.md) notas EE debe registrarse como un generador de clases con el common language runtime y el entornos en tiempo de ejecución de Visual Studio.

 [Implementar un evaluador de expresiones](../../extensibility/debugger/implementing-an-expression-evaluator.md) describe cómo el proceso de evaluar una expresión incluye en el motor de depuración (DE), el proveedor de símbolos (SP), el objeto de enlazador y el evaluador de expresiones (EE).

 [Mostrar variables locales](../../extensibility/debugger/displaying-locals.md) describe cómo, cuando la ejecución se detiene, el paquete de depuración llama a la DE para obtener una lista de argumentos y variables locales.

 [Evaluar una expresión de la ventana Inspección](../../extensibility/debugger/evaluating-a-watch-window-expression.md) documenta cómo el paquete de depuración de Visual Studio llama a la DE para determinar el valor actual de cada expresión en su lista de supervisión.

 [Cambie el valor de una variable local](../../extensibility/debugger/changing-the-value-of-a-local.md) explica que cambiar el valor de una variable local, cada línea de la ventana variables locales tiene asociado un objeto que proporciona el nombre, el tipo y el valor actual de una variable local.

 [Implementar los visualizadores de tipo y visores personalizados](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md) explica qué interfaz debe implementarse mediante los componentes que admiten visualizadores de tipo y visores personalizados.

## <a name="see-also"></a>Vea también
 [Extensibilidad del depurador de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)