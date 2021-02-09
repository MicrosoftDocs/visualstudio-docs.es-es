---
title: Arquitectura del evaluador de expresiones | Microsoft Docs
description: Obtenga información sobre cómo integrar un lenguaje patentado en el paquete de depuración de Visual Studio, incluidas las interfaces del evaluador de expresiones y del proveedor de símbolos y del enlazador.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- architecture, expression evaluators
- expression evaluators, architecture
- debugging [Debugging SDK], expression evaluators
ms.assetid: aad7c4c6-1dc1-4d32-b975-f1fdf76bdeda
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ac81d386f0e1104879701faba230d5384259fa25
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921408"
---
# <a name="expression-evaluator-architecture"></a>Arquitectura del evaluador de expresiones
> [!IMPORTANT]
> En Visual Studio 2015, esta manera de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, consulte [evaluadores](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) de expresiones CLR y [ejemplo de evaluador de expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 La integración de un lenguaje patentado en el paquete de depuración de Visual Studio significa que debe configurar las interfaces del evaluador de expresiones necesarias (EE) y llamar a las interfaces del proveedor de símbolos en tiempo de ejecución (SP) de Common Language Runtime y del enlazador. Los objetos SP y Binder, junto con la dirección de ejecución actual, son el contexto en el que se evalúan las expresiones. La información que estas interfaces generan y consumen representa los conceptos clave de la arquitectura de EE.

## <a name="overview"></a>Información general

### <a name="parse-the-expression"></a>Analizar la expresión
 Al depurar un programa, las expresiones se evalúan por varios motivos, pero siempre cuando el programa que se está depurando se ha detenido en un punto de interrupción (un punto de interrupción colocado por el usuario o uno provocado por una excepción). En este momento, Visual Studio obtiene un marco de pila, tal como se representa en la interfaz [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) , del motor de depuración (de). A continuación, Visual Studio llama a [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) para obtener la interfaz [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) . Esta interfaz representa un contexto en el que se pueden evaluar las expresiones; [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) es el punto de entrada al proceso de evaluación. Hasta este momento, se implementan todas las interfaces mediante el DE.

 Cuando `IDebugExpressionContext2::ParseText` se llama a, el objeto de crea una instancia de EE asociada al lenguaje del archivo de código fuente donde se produjo el punto de interrupción (de también crea una instancia de SH en este momento). El EE se representa mediante la interfaz [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md) . A continuación, el DE llama a [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) para convertir la expresión (en formato de texto) en una expresión analizada, lista para su evaluación. Esta expresión analizada se representa mediante la interfaz [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) . La expresión se analiza normalmente y no se evalúa en este punto.

 El DE crea un objeto que implementa la interfaz [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) , coloca el `IDebugParsedExpression` objeto en el `IDebugExpression2` objeto y devuelve el `IDebugExpression2` objeto de `IDebugExpressionContext2::ParseText` .

### <a name="evaluate-the-expression"></a>Evaluación de la expresión
 Visual Studio llama a [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) para evaluar la expresión analizada. Ambos métodos llaman a [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) ( `IDebugExpression2::EvaluateSync` llama al método inmediatamente, mientras `IDebugExpression2::EvaluateAsync` que llama al método a través de un subproceso en segundo plano) para evaluar la expresión analizada y devolver una interfaz [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) que representa el valor y el tipo de la expresión analizada. `IDebugParsedExpression::EvaluateSync` usa el enlazador SH, address y BINDER proporcionado para convertir la expresión analizada en un valor real, representado por la `IDebugProperty2` interfaz.

### <a name="for-example"></a>Por ejemplo
 Una vez que se alcanza un punto de interrupción en un programa en ejecución, el usuario elige ver una variable en el cuadro de diálogo **Inspección rápida** . Este cuadro de diálogo muestra el nombre de la variable, su valor y su tipo. Normalmente, el usuario puede cambiar el valor.

 Cuando se muestra el cuadro de diálogo **Inspección rápida** , el nombre de la variable que se está examinando se envía como texto a [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Esto devuelve un objeto [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) que representa la expresión analizada, en este caso, la variable. A continuación, se llama a [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) para generar un `IDebugProperty2` objeto que representa el tipo y el valor de la variable, así como su nombre. Esta es la información que se muestra.

 Si el usuario cambia el valor de la variable, se llama a [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) con el nuevo valor, que cambia el valor de la variable en memoria, por lo que se usará cuando el programa se reanude la ejecución.

 Vea [Mostrar variables locales](../../extensibility/debugger/displaying-locals.md) para obtener más detalles sobre este proceso de visualización de los valores de las variables. Vea [cambiar el valor de una variable local](../../extensibility/debugger/changing-the-value-of-a-local.md) para obtener más información sobre cómo se cambia el valor de una variable.

## <a name="in-this-section"></a>En esta sección
 [Contexto de evaluación](../../extensibility/debugger/evaluation-context.md) Proporciona los argumentos que se pasan cuando el DE llama a EE.

 [Interfaces del evaluador de expresiones clave](../../extensibility/debugger/key-expression-evaluator-interfaces.md) Describe las interfaces cruciales necesarias al escribir un EE, junto con el contexto de evaluación.

## <a name="see-also"></a>Vea también
- [Escribir un evaluador de expresiones CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Mostrar variables locales](../../extensibility/debugger/displaying-locals.md)
- [Cambiar el valor de una variable local](../../extensibility/debugger/changing-the-value-of-a-local.md)
