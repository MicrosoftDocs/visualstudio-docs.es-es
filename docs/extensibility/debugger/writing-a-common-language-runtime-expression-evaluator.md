---
title: Escribir un evaluador de expresiones de Common Language Runtime ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators, tutorial
- expression evaluation, samples
- debugging [Debugging SDK], expression evaluators tutorial
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e46eaef395a7c66792662b3c5d4b9fbad419dfb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712323"
---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>Escribir un evaluador de expresiones de Common Language Runtime
> [!IMPORTANT]
> En Visual Studio 2015, esta forma de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, vea Evaluadores de [expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y Ejemplo de evaluador de [expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 El evaluador de expresiones (EE) es la parte de un motor de depuración (DE) que controla la sintaxis y la semántica del lenguaje de programación que produjo el código que se está depurando. Las expresiones deben evaluarse en el contexto de un lenguaje de programación. Por ejemplo, en algunos idiomas, la expresión "A+B" significa "la suma de A y B." En otros idiomas, la misma expresión podría significar "A o B." Por lo tanto, se debe escribir un EE independiente para cada lenguaje de programación que genera código de objeto que se va a depurar en el IDE de Visual Studio.

 Algunos aspectos del paquete de depuración de Visual Studio deben interpretar el código en el contexto del lenguaje de programación. Por ejemplo, cuando la ejecución se detiene en un punto de interrupción, se deben evaluar y mostrar todas las expresiones que el usuario haya escrito en una ventana **Inspección.** El usuario puede cambiar el valor de una variable local escribiendo una expresión en una ventana **Inspección** o en la ventana **Inmediato.**

## <a name="in-this-section"></a>En esta sección
 [Common Language Runtime y evaluación de expresiones](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md) Explica que cuando se integra el lenguaje de programación propietario en el IDE de Visual Studio, escribir un EE capaz de evaluar expresiones en el contexto del lenguaje propietario le permite compilar en un lenguaje intermedio de Microsoft (MSIL) sin escribir un motor de depuración.

 [Arquitectura del evaluador](../../extensibility/debugger/expression-evaluator-architecture.md) de expresiones Describe cómo implementar las interfaces EE necesarias y llamar al proveedor de símbolos de Common Language Runtime (SP) y a las interfaces de enlazador.

 [Registrar un evaluador](../../extensibility/debugger/registering-an-expression-evaluator.md) de expresiones Tenga en cuenta que el EE debe registrarse como un generador de clases con common Language Runtime y entornos de tiempo de ejecución de Visual Studio.

 [Implementar un evaluador](../../extensibility/debugger/implementing-an-expression-evaluator.md) de expresiones Describe cómo el proceso de evaluación de una expresión incluye el motor de depuración (DE), el proveedor de símbolos (SP), el objeto de enlazador y el evaluador de expresiones (EE).

 [Mostrar locales](../../extensibility/debugger/displaying-locals.md) Describe cómo, cuando se detiene la ejecución, el paquete de depuración llama a la DE para obtener una lista de variables y argumentos locales.

 [Evaluar una expresión de ventana de inspección](../../extensibility/debugger/evaluating-a-watch-window-expression.md) Documenta cómo el paquete de depuración de Visual Studio llama a la DE para determinar el valor actual de cada expresión en su lista de inspección.

 [Cambiar el valor de un local](../../extensibility/debugger/changing-the-value-of-a-local.md) Explica que al cambiar el valor de un local, cada línea de la ventana Locales tiene un objeto asociado que proporciona el nombre, el tipo y el valor actual de un local.

 [Implementar visualizadores de tipos y visores personalizados](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md) Explica qué interfaz debe implementarse mediante el componente para admitir visualizadores de tipos y visores personalizados.

## <a name="see-also"></a>Vea también
 [Extensibilidad del depurador de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
