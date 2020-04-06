---
title: Interfaces del evaluador de expresiones clave (Key Expression Evaluator Interfaces) Microsoft Docs
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
ms.openlocfilehash: 01527edac4000f0b2f7b89fdd507fc093f0d7734
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738493"
---
# <a name="key-expression-evaluator-interfaces"></a>Interfaces del evaluador de expresiones clave
> [!IMPORTANT]
> En Visual Studio 2015, esta forma de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, consulte Evaluadores de [expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y Ejemplo de evaluador de [expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Al escribir un evaluador de expresiones (EE), junto con el contexto de evaluación, debe estar familiarizado con las interfaces siguientes.

## <a name="interface-descriptions"></a>Descripciones de la interfaz

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

     Tiene un único método, [GetAddress](../../extensibility/debugger/reference/idebugaddress-getaddress.md), que obtiene una estructura de datos que representa el punto actual de ejecución. Esta estructura de datos es uno de los tres argumentos que el motor de depuración (DE) pasa al método [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) para evaluar una expresión. Esta interfaz normalmente la implementa el proveedor de símbolos.

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

     Tiene el [bind](../../extensibility/debugger/reference/idebugbinder-bind.md) método, que obtiene el área de memoria que contiene el valor actual de un símbolo. Dado el método contenedor, representado por un [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) objeto y el propio símbolo, `IDebugBinder::Bind` representado por un [IDebugField](../../extensibility/debugger/reference/idebugfield.md) objeto, devuelve el valor del símbolo. `IDebugBinder`normalmente es implementado por el DE.

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

     Representa un tipo de datos simple. Para tipos más complejos, como matrices y métodos, use las derivadas [IDebugArrayField](../../extensibility/debugger/reference/idebugarrayfield.md) y [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) interfaces, respectivamente. [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) es otra interfaz derivada importante que representa símbolos que contienen otros símbolos, como métodos o clases. La `IDebugField` interfaz (y sus derivados) normalmente la implementa el proveedor de símbolos.

     Un `IDebugField` objeto se puede utilizar para buscar el nombre y el tipo de un símbolo y, junto con un [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) objeto, se puede utilizar para buscar su valor.

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

     Representa los bits reales del valor en tiempo de ejecución de un símbolo. [Bind](../../extensibility/debugger/reference/idebugbinder-bind.md) toma un [IDebugField](../../extensibility/debugger/reference/idebugfield.md) objeto, que representa un símbolo y devuelve un [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) objeto. El [GetValue](../../extensibility/debugger/reference/idebugobject-getvalue.md) método devuelve el valor del símbolo en un búfer de memoria. Un DE normalmente implementa esta interfaz para representar el valor de una propiedad en la memoria.

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

     Esta interfaz representa el propio evaluador de expresiones. El método de clave es [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md), que devuelve una interfaz [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) .

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

     Esta interfaz representa una expresión analizada lista para evaluarse. El método clave es [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) que devuelve un IDebugProperty2 que representa el valor y el tipo de la expresión.

- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)

     Esta interfaz representa un valor y su tipo y es el resultado de una evaluación de expresiones.

## <a name="see-also"></a>Vea también
- [Contexto de evaluación](../../extensibility/debugger/evaluation-context.md)
