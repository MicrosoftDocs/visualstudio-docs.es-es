---
title: Arquitectura del evaluador de expresiones (Expression Evaluator Architecture) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- architecture, expression evaluators
- expression evaluators, architecture
- debugging [Debugging SDK], expression evaluators
ms.assetid: aad7c4c6-1dc1-4d32-b975-f1fdf76bdeda
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aac782c653f230d5598a49d43eb70f548de6dc41
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738699"
---
# <a name="expression-evaluator-architecture"></a>Arquitectura del evaluador de expresiones
> [!IMPORTANT]
> En Visual Studio 2015, esta forma de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, vea Evaluadores de [expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y Ejemplo de evaluador de [expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 La integración de un lenguaje propietario en el paquete de depuración de Visual Studio significa que debe configurar las interfaces de evaluador de expresiones (EE) necesarias y llamar al proveedor de símbolos en tiempo de ejecución (SP) de lenguaje común e interfaces de enlazador. Los objetos SP y binder, junto con la dirección de ejecución actual, son el contexto en el que se evalúan las expresiones. La información que estas interfaces producen y consumen representa los conceptos clave en la arquitectura de un EE.

## <a name="overview"></a>Información general

### <a name="parse-the-expression"></a>Analizar la expresión
 Al depurar un programa, las expresiones se evalúan por varias razones, pero siempre cuando el programa que se está depurando se ha detenido en un punto de interrupción (ya sea un punto de interrupción colocado por el usuario o uno causado por una excepción). Es en este momento cuando Visual Studio obtiene un marco de pila, representado por el [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) interfaz, desde el motor de depuración (DE). Visual Studio, a continuación, llama a [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) para obtener el [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaz. Esta interfaz representa un contexto en el que se pueden evaluar expresiones; [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) es el punto de entrada al proceso de evaluación. Hasta este punto, todas las interfaces son implementadas por el DE.

 Cuando `IDebugExpressionContext2::ParseText` se llama, el DE crea una instancia del EE asociado con el idioma del archivo de origen donde se produjo el punto de interrupción (el DE también crea una instancia de la SH en este punto). El EE se representa mediante el [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md) interfaz. A continuación, el DE llama a [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) para convertir la expresión (en forma de texto) en una expresión analizada, lista para la evaluación. Esta expresión analizada se representa mediante el [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) interfaz. Normalmente, la expresión se analiza y no se evalúa en este momento.

 La DE crea un objeto que implementa el [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) `IDebugExpression2` interfaz, coloca `IDebugExpression2` el `IDebugExpressionContext2::ParseText` `IDebugParsedExpression` objeto en el objeto y devuelve el objeto desde .

### <a name="evaluate-the-expression"></a>Evaluar la expresión
 Visual Studio llama a [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) para evaluar la expresión analizada. Ambos métodos llaman a`IDebugExpression2::EvaluateSync` [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) ( `IDebugExpression2::EvaluateAsync` llama al método inmediatamente, mientras que llama al método a través de un subproceso en segundo plano) para evaluar la expresión analizada y devolver un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfaz que representa el valor y el tipo de la expresión analizada. `IDebugParsedExpression::EvaluateSync`utiliza el SH, la dirección y el enlazador proporcionados para convertir `IDebugProperty2` la expresión analizada en un valor real, representado por la interfaz.

### <a name="for-example"></a>Por ejemplo
 Después de alcanzar un punto de interrupción en un programa en ejecución, el usuario elige ver una variable en el cuadro de diálogo **Inspección rápida.** Este cuadro de diálogo muestra el nombre de la variable, su valor y su tipo. Normalmente, el usuario puede cambiar el valor.

 Cuando se muestra el cuadro de diálogo **Inspección rápida,** el nombre de la variable que se examina se envía como texto a [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Esto devuelve un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) objeto que representa la expresión analizada, en este caso, la variable. [A](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) continuación, se llama `IDebugProperty2` a EvaluateSync para generar un objeto que representa el valor y el tipo de la variable, así como su nombre. Es esta información la que se muestra.

 Si el usuario cambia el valor de la variable, [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) se llama con el nuevo valor, que cambia el valor de la variable en la memoria para que se usará cuando el programa reanude la ejecución.

 Consulte Visualización de [valores locales](../../extensibility/debugger/displaying-locals.md) para obtener más detalles sobre este proceso de visualización de los valores de las variables. Consulte [Cambiar el valor de un local](../../extensibility/debugger/changing-the-value-of-a-local.md) para obtener más detalles sobre cómo se cambia el valor de una variable.

## <a name="in-this-section"></a>En esta sección
 [Contexto de evaluación](../../extensibility/debugger/evaluation-context.md) Proporciona los argumentos que se pasan cuando el DE llama a EE.

 [Interfaces del evaluador](../../extensibility/debugger/key-expression-evaluator-interfaces.md) de expresiones clave Describe las interfaces cruciales necesarias al escribir un EE, junto con el contexto de evaluación.

## <a name="see-also"></a>Vea también
- [Escribir un evaluador de expresiones CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Mostrando locales](../../extensibility/debugger/displaying-locals.md)
- [Cambiar el valor de un local](../../extensibility/debugger/changing-the-value-of-a-local.md)
