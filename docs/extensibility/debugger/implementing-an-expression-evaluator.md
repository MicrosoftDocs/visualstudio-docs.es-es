---
title: Implementación de un evaluador de expresiones Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a8c7c9a1130794dd4c28f212afd6cb3c030f5a1b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738544"
---
# <a name="implement-an-expression-evaluator"></a>Implementar un evaluador de expresiones
> [!IMPORTANT]
> En Visual Studio 2015, esta forma de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, vea Evaluadores de [expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y Ejemplo de evaluador de [expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 La evaluación de una expresión es una interacción compleja entre el motor de depuración (DE), el proveedor de símbolos (SP), el objeto de enlazador y el evaluador de expresiones (EE). Estos cuatro componentes están conectados por interfaces que son implementadas por un componente y consumidas por otro.

 El EE toma una expresión de la DE en forma de una cadena y la analiza o evalúa. El EE ejecuta las siguientes interfaces, que son consumidas por el DE:

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

  El EE llama al objeto de enlazador, proporcionado por el DE, para obtener el valor de símbolos y objetos. El EE consume las siguientes interfaces, que son implementadas por el DE:

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

- [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)

- [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)

- [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)

- [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)

- [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

  El EE ejecuta [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md). `IDebugProperty2`proporciona el mecanismo para describir el resultado de una evaluación de expresión, como una variable local, una primitiva o un objeto a Visual Studio, que, a continuación, muestra la información adecuada en la ventana **Locales**, **Inspección**o **Inmediato.**

  El SP es dado al EE por el DE cuando pide información. El SP ejecuta interfaces que describen direcciones y campos, como las interfaces siguientes y sus derivados:

- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

  El EE consume todas estas interfaces.

## <a name="in-this-section"></a>En esta sección
 [Estrategia de implementación del evaluador](../../extensibility/debugger/expression-evaluator-implementation-strategy.md) de expresiones Define un proceso de tres pasos para la estrategia de implementación del evaluador de expresiones (EE).

## <a name="see-also"></a>Vea también
- [Escribir un evaluador de expresiones CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
