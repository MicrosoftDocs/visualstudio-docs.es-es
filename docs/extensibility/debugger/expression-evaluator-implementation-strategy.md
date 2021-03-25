---
title: Estrategia de implementación del evaluador de expresiones | Microsoft Docs
description: Obtenga información sobre una estrategia para crear un evaluador de expresiones implementando primero el código para mostrar las variables locales en la ventana variables locales.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d10ce818e9df370b4484a0250525dbe9482b8b2c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054990"
---
# <a name="expression-evaluator-implementation-strategy"></a>Estrategia de implementación del evaluador de expresiones
> [!IMPORTANT]
> En Visual Studio 2015, esta manera de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, consulte [evaluadores](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) de expresiones CLR y [ejemplo de evaluador de expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Un enfoque para crear rápidamente un evaluador de expresiones (EE) es primero implementar el código mínimo necesario para mostrar las variables locales en la ventana **variables** locales. Resulta útil saber que cada línea de la ventana **variables locales** muestra el nombre, el tipo y el valor de una variable local, y que los tres se representan mediante un objeto [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) . El nombre, el tipo y el valor de una variable local se obtienen de un `IDebugProperty2` objeto llamando a su método [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) . Para obtener más información sobre cómo mostrar las variables locales en la ventana **variables** locales, vea [Mostrar variables locales](../../extensibility/debugger/displaying-locals.md).

## <a name="discussion"></a>Debate
 Una posible secuencia de implementación comienza con la implementación de [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md). Los métodos [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) y [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) se deben implementar para mostrar variables locales. La llamada a `IDebugExpressionEvaluator::GetMethodProperty` devuelve un `IDebugProperty2` objeto que representa un método: es decir, un objeto [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) . Los propios métodos no se muestran en la ventana **variables locales** .

 El método [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) debe implementarse a continuación. El motor de depuración (DE) llama a este método para obtener una lista de variables locales y argumentos pasando `IDebugProperty2::EnumChildren` un `guidFilter` argumento de `guidFilterLocalsPlusArgs` . `IDebugProperty2::EnumChildren` llama a [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) y [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md), combinando los resultados en una sola enumeración. Consulte [Mostrar variables locales](../../extensibility/debugger/displaying-locals.md) para obtener más detalles.

## <a name="see-also"></a>Consulte también
- [Implementar un evaluador de expresiones](../../extensibility/debugger/implementing-an-expression-evaluator.md)
- [Mostrar variables locales](../../extensibility/debugger/displaying-locals.md)
