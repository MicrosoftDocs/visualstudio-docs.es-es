---
title: Implementación de un evaluador de expresiones | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 66a1a0cb78036982923d20e39a3a4c32b288e459
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66326210"
---
# <a name="implement-an-expression-evaluator"></a>Implementar un evaluador de expresiones
> [!IMPORTANT]
> En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [ejemplo de evaluador de expresión administrado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Evaluar una expresión es una interacción compleja entre el motor de depuración (DE), el proveedor de símbolos (SP), el objeto de enlazador y el evaluador de expresiones (EE). Estos cuatro componentes están conectados mediante las interfaces que implementa un componente y consumidas por otro.

 EE toma una expresión de la DE en forma de cadena y analiza ni lo evalúa. EE ejecuta las siguientes interfaces, que consuman la DE:

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

  EE llama al objeto de enlazador, proporcionado por la DE obtener el valor de símbolos y objetos. EE consume las interfaces siguientes, que se implementan mediante la DE:

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

- [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)

- [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)

- [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)

- [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)

- [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

  Se ejecuta el EE [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md). `IDebugProperty2` proporciona el mecanismo para describir el resultado de evaluación de una expresión, como una variable local, un tipo primitivo o un objeto en Visual Studio, que, a continuación, muestra la información correspondiente en el **variables locales**, **inspección** , o **inmediato** ventana.

  SP asignado a la EE por la DE cuando solicita información. SP ejecuta a las interfaces que describen direcciones y campos, como las siguientes interfaces y sus derivados:

- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

  EE consume todas estas interfaces.

## <a name="in-this-section"></a>En esta sección
 [Estrategia de implementación del evaluador de expresiones](../../extensibility/debugger/expression-evaluator-implementation-strategy.md) define un proceso de tres pasos para la estrategia de implementación de expresión del evaluador de expresiones (EE).

## <a name="see-also"></a>Vea también
- [Escribir un evaluador de expresiones CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)