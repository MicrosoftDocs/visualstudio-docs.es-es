---
title: Interfaces del evaluador de expresiones clave | Microsoft Docs
description: Obtenga información sobre las interfaces que debe conocer al escribir un evaluador de expresiones, junto con el contexto de evaluación.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, interfaces
ms.assetid: 1cac9aa3-0867-4e12-a16e-1e90abbc0fb6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5693ebee96428b343da2bb14202ffef06fd6dd81
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606689"
---
# <a name="key-expression-evaluator-interfaces"></a>Interfaces del evaluador de expresiones clave
> [!IMPORTANT]
> En Visual Studio 2015, esta manera de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, consulte [evaluadores](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) de expresiones CLR y [ejemplo de evaluador de expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Al escribir un evaluador de expresiones (EE), junto con el contexto de evaluación, debería estar familiarizado con las interfaces siguientes.

## <a name="interface-descriptions"></a>Descripciones de interfaz

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

     Tiene un único método, [GetAddress](../../extensibility/debugger/reference/idebugaddress-getaddress.md), que obtiene una estructura de datos que representa el punto de ejecución actual. Esta estructura de datos es uno de los tres argumentos que el motor DE depuración (DE) pasa al método [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) para evaluar una expresión. Normalmente, el proveedor de símbolos implementa esta interfaz.

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

     Tiene el método [BIND](../../extensibility/debugger/reference/idebugbinder-bind.md) , que obtiene el área de memoria que contiene el valor actual de un símbolo. Dado el método contenedor, representado por un objeto [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) , y el propio símbolo, representado por un objeto [IDebugField](../../extensibility/debugger/reference/idebugfield.md) , `IDebugBinder::Bind` devuelve el valor del símbolo. `IDebugBinder` se implementa normalmente por parte DE.

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

     Representa un tipo de datos simple. Para tipos más complejos, como matrices y métodos, use las interfaces derivadas [IDebugArrayField](../../extensibility/debugger/reference/idebugarrayfield.md) y [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) , respectivamente. [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) es otra interfaz derivada importante que representa símbolos que contienen otros símbolos, como métodos o clases. Normalmente, el `IDebugField` proveedor de símbolos implementa la interfaz (y sus derivados).

     Un `IDebugField` objeto se puede usar para buscar el nombre y el tipo de un símbolo y, junto con un objeto [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) , se puede usar para buscar su valor.

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

     Representa los bits reales del valor en tiempo de ejecución de un símbolo. [BIND](../../extensibility/debugger/reference/idebugbinder-bind.md) toma un objeto [IDebugField](../../extensibility/debugger/reference/idebugfield.md) , que representa un símbolo, y devuelve un objeto [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) . El método [GetValue](../../extensibility/debugger/reference/idebugobject-getvalue.md) devuelve el valor del símbolo en un búfer de memoria. Un DE normalmente implementa esta interfaz para representar el valor de una propiedad en la memoria.

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

     Esta interfaz representa el evaluador de expresiones. El método clave es [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md), que devuelve una interfaz [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) .

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

     Esta interfaz representa una expresión analizada lista para su evaluación. El método clave es [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) , que devuelve un IDebugProperty2 que representa el valor y el tipo de la expresión.

- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)

     Esta interfaz representa un valor y su tipo y es el resultado de una evaluación de expresión.

## <a name="see-also"></a>Consulte también
- [Contexto de evaluación](../../extensibility/debugger/evaluation-context.md)
