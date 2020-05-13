---
title: Estrategia de Implementación del Evaluador de Expresiones (Expression Evaluator Implementation Strategy) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3922689c20c839b3c0c2b2440bc9fefd5d25c80a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738673"
---
# <a name="expression-evaluator-implementation-strategy"></a>Estrategia de implementación del evaluador de expresiones
> [!IMPORTANT]
> En Visual Studio 2015, esta forma de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, vea Evaluadores de [expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y Ejemplo de evaluador de [expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Un enfoque para crear rápidamente un evaluador de expresiones (EE) es implementar primero el código mínimo necesario para mostrar variables locales en la ventana **Locales.** Es útil tener en cuenta que cada línea de la ventana **Locales** muestra el nombre, el tipo y el valor de una variable local y que los tres están representados por un objeto [IDebugProperty2.](../../extensibility/debugger/reference/idebugproperty2.md) El nombre, el tipo y el valor de `IDebugProperty2` una variable local se obtiene de un objeto mediante una llamada a su [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) método. Para obtener más información sobre cómo mostrar variables locales en la ventana **Locales,** consulte [Visualización de variables locales](../../extensibility/debugger/displaying-locals.md).

## <a name="discussion"></a>Discusión
 Una posible secuencia de implementación comienza con la implementación de [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md). Los métodos [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) y [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) deben implementarse para mostrar los locales. Llamar `IDebugExpressionEvaluator::GetMethodProperty` devuelve `IDebugProperty2` un objeto que representa un método: es decir, un [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) objeto. Los propios métodos no se muestran en la ventana **Locales.**

 El [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) método debe implementarse a continuación. El motor de depuración (DE) llama a este método para `IDebugProperty2::EnumChildren` `guidFilter` obtener `guidFilterLocalsPlusArgs`una lista de variables y argumentos locales pasando un argumento de . `IDebugProperty2::EnumChildren`llama a [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) y [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md), combinando los resultados en una sola enumeración. Consulte [Mostrar configuraciones regionales](../../extensibility/debugger/displaying-locals.md) para obtener más detalles.

## <a name="see-also"></a>Vea también
- [Implementar un evaluador de expresiones](../../extensibility/debugger/implementing-an-expression-evaluator.md)
- [Mostrar locales](../../extensibility/debugger/displaying-locals.md)
