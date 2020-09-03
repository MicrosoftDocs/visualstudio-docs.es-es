---
title: Escribir un evaluador de expresiones de Common Language Runtime | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712323"
---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>Escribir un evaluador de expresiones de Common Language Runtime
> [!IMPORTANT]
> En Visual Studio 2015, esta manera de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, consulte [evaluadores](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) de expresiones CLR y [ejemplo de evaluador de expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 El evaluador de expresiones (EE) es la parte de un motor de depuración (DE) que controla la sintaxis y la semántica del lenguaje de programación que generó el código que se está depurando. Las expresiones deben evaluarse en el contexto de un lenguaje de programación. Por ejemplo, en algunos lenguajes, la expresión "A + B" significa "la suma de A y B". En otros lenguajes, la misma expresión podría significar "A o B". Por lo tanto, se debe escribir un EE independiente para cada lenguaje de programación que genera código de objeto que se va a depurar en el IDE de Visual Studio.

 Algunos aspectos del paquete de depuración de Visual Studio deben interpretar el código en el contexto del lenguaje de programación. Por ejemplo, cuando la ejecución se detiene en un punto de interrupción, las expresiones que el usuario ha escrito en una ventana de **inspección** deben evaluarse y mostrarse. El usuario puede cambiar el valor de una variable local escribiendo una expresión en una ventana **inspección** o en la ventana **inmediato** .

## <a name="in-this-section"></a>En esta sección
 [Common Language Runtime y evaluación de expresiones](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md) Explica que cuando se está integrando el lenguaje de programación de propiedad en el IDE de Visual Studio, escribir una capaz de evaluar las expresiones en el contexto del lenguaje de propiedad le permite compilar en un lenguaje intermedio de Microsoft (MSIL) sin necesidad de escribir un motor de depuración.

 [Arquitectura del evaluador de expresiones](../../extensibility/debugger/expression-evaluator-architecture.md) Describe cómo implementar las interfaces de EE necesarias y llamar a las interfaces del proveedor de símbolos Common Language Runtime (SP) y del enlazador.

 [Registrar un evaluador de expresiones](../../extensibility/debugger/registering-an-expression-evaluator.md) Notas que el EE debe registrarse como un generador de clases con los entornos de tiempo de ejecución de Common Language Runtime y Visual Studio.

 [Implementar un evaluador de expresiones](../../extensibility/debugger/implementing-an-expression-evaluator.md) Describe cómo el proceso de evaluación de una expresión incluye el motor de depuración (DE), el proveedor de símbolos (SP), el objeto de enlazador y el evaluador de expresiones (EE).

 [Mostrar variables locales](../../extensibility/debugger/displaying-locals.md) Describe cómo, cuando la ejecución se pausa, el paquete DE depuración llama a DE para obtener una lista de variables locales y argumentos.

 [Evaluar una expresión de la ventana Inspección](../../extensibility/debugger/evaluating-a-watch-window-expression.md) Documenta cómo llama el paquete DE depuración DE Visual Studio al DE para determinar el valor actual de cada expresión en su lista de inspección.

 [Cambiar el valor de una variable local](../../extensibility/debugger/changing-the-value-of-a-local.md) Explica que, al cambiar el valor de una variable local, cada línea de la ventana variables locales tiene un objeto asociado que proporciona el nombre, el tipo y el valor actual de un local.

 [Implementar visualizadores de tipos y visores personalizados](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md) Explica qué interfaz debe implementar cada componente para admitir visualizadores de tipo y visores personalizados.

## <a name="see-also"></a>Vea también
 [Extensibilidad del depurador de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
