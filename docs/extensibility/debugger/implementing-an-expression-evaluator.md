---
title: Implementar un evaluador de expresiones | Microsoft Docs
description: Obtenga información sobre la evaluación de una expresión, que implica el motor de depuración, el proveedor de símbolos, el objeto de enlazador y el evaluador de expresiones.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 28989178ab726a9b274f66e0a9296f2bf49ead4a
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2020
ms.locfileid: "96559971"
---
# <a name="implement-an-expression-evaluator"></a>Implementar un evaluador de expresiones
> [!IMPORTANT]
> En Visual Studio 2015, esta manera de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, consulte [evaluadores](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) de expresiones CLR y [ejemplo de evaluador de expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 La evaluación de una expresión es una interacción compleja entre el motor DE depuración (DE), el proveedor de símbolos (SP), el objeto de enlazador y el evaluador de expresiones (EE). Estos cuatro componentes están conectados mediante interfaces implementadas por un componente y consumidos por otro.

 El EE toma una expresión de de la forma de una cadena y la analiza o la evalúa. El código de EE ejecuta las siguientes interfaces, que son utilizadas por el:

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

  El EE llama al objeto Binder, proporcionado por DE, para obtener el valor de Symbols y Objects. EE usa las siguientes interfaces, que son implementadas por el DE:

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

- [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)

- [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)

- [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)

- [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)

- [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

  El EE. ejecuta [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md). `IDebugProperty2` proporciona el mecanismo para describir el resultado de una evaluación de expresión, como una variable local, un tipo primitivo o un objeto en Visual Studio, que, a continuación, muestra la información adecuada en las ventanas **variables locales**, **inspección** o **inmediato** .

  El SP se asigna al de EE por el DE cuando solicita información. El SP ejecuta interfaces que describen direcciones y campos, como las siguientes interfaces y sus derivados:

- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

  EE usa todas estas interfaces.

## <a name="in-this-section"></a>En esta sección
 [Estrategia de implementación del evaluador de expresiones](../../extensibility/debugger/expression-evaluator-implementation-strategy.md) Define un proceso de tres pasos para la estrategia de implementación del evaluador de expresiones (EE).

## <a name="see-also"></a>Vea también
- [Escribir un evaluador de expresiones CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
