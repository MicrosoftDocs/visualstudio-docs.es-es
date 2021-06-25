---
title: Interfaces del evaluador de expresiones clave | Microsoft Docs
description: Obtenga información sobre las interfaces con las que debe estar familiarizado al escribir un evaluador de expresiones, junto con el contexto de evaluación.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, interfaces
ms.assetid: 1cac9aa3-0867-4e12-a16e-1e90abbc0fb6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: abfa4018e763bbbac5ff788f401d0ceb76eb97a1
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901271"
---
# <a name="key-expression-evaluator-interfaces"></a>Interfaces del evaluador de expresiones clave
> [!IMPORTANT]
> En Visual Studio 2015, esta forma de implementar evaluadores de expresiones está en desuso. Para obtener información sobre cómo implementar evaluadores de expresiones CLR, vea Evaluadores de [expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y Ejemplo de [evaluador de expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Al escribir un evaluador de expresiones (EE), junto con el contexto de evaluación, debe estar familiarizado con las interfaces siguientes.

## <a name="interface-descriptions"></a>Descripciones de interfaz

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

     Tiene un único método, [GetAddress](../../extensibility/debugger/reference/idebugaddress-getaddress.md), que obtiene una estructura de datos que representa el punto de ejecución actual. Esta estructura de datos es uno de los tres argumentos que el motor de depuración (DE) pasa al método [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) para evaluar una expresión. Normalmente, el proveedor de símbolos implementa esta interfaz.

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

     Tiene el [método Bind,](../../extensibility/debugger/reference/idebugbinder-bind.md) que obtiene el área de memoria que contiene el valor actual de un símbolo. Dado el método que lo contiene, representado por un objeto [IDebugObject,](../../extensibility/debugger/reference/idebugobject.md) y el propio símbolo, representado por un [objeto IDebugField,](../../extensibility/debugger/reference/idebugfield.md) devuelve el valor `IDebugBinder::Bind` del símbolo. `IDebugBinder` normalmente se implementa mediante el DE.

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

     Representa un tipo de datos simple. Para tipos más complejos, como matrices y métodos, use las interfaces [IDebugArrayField](../../extensibility/debugger/reference/idebugarrayfield.md) e [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) derivadas, respectivamente. [IDebugContainerField es](../../extensibility/debugger/reference/idebugcontainerfield.md) otra interfaz derivada importante que representa los símbolos que contienen otros símbolos, como métodos o clases. La `IDebugField` interfaz (y sus derivados) normalmente se implementa mediante el proveedor de símbolos.

     Un objeto se puede usar para buscar el nombre y el tipo de un símbolo y, junto con un `IDebugField` [objeto IDebugBinder,](../../extensibility/debugger/reference/idebugbinder.md) se puede usar para buscar su valor.

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

     Representa los bits reales del valor en tiempo de ejecución de un símbolo. [Bind](../../extensibility/debugger/reference/idebugbinder-bind.md) toma un [objeto IDebugField,](../../extensibility/debugger/reference/idebugfield.md) que representa un símbolo, y devuelve un [objeto IDebugObject.](../../extensibility/debugger/reference/idebugobject.md) El [método GetValue](../../extensibility/debugger/reference/idebugobject-getvalue.md) devuelve el valor del símbolo en un búfer de memoria. Normalmente, un DE implementa esta interfaz para representar el valor de una propiedad en memoria.

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

     Esta interfaz representa el propio evaluador de expresiones. El método clave es [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md), que devuelve una [interfaz IDebugParsedExpression.](../../extensibility/debugger/reference/idebugparsedexpression.md)

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

     Esta interfaz representa una expresión analizada lista para evaluarse. El método clave [es EvaluateSync,](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) que devuelve un IDebugProperty2 que representa el valor y el tipo de la expresión.

- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)

     Esta interfaz representa un valor y su tipo y es el resultado de una evaluación de expresión.

## <a name="see-also"></a>Consulta también
- [Contexto de evaluación](../../extensibility/debugger/evaluation-context.md)
