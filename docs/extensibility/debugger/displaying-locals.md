---
title: Visualización de locales ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, displaying locals
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4d44b276aeb9c6acb0ef34cc186662d49246de7d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738930"
---
# <a name="display-locals"></a>Mostrar locales
> [!IMPORTANT]
> En Visual Studio 2015, esta forma de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, vea Evaluadores de [expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y Ejemplo de evaluador de [expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 La ejecución siempre tiene lugar en el contexto de un método, también conocido como método contenedor o método actual. Cuando se detiene la ejecución, Visual Studio llama al motor de depuración (DE) para obtener una lista de variables y argumentos locales, denominados colectivamente los valores locales del método. Visual Studio muestra estos valores locales y sus valores en la ventana **Locales.**

 Para mostrar los locales, el DE llama a la [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) método que pertenece a la EE y le proporciona un contexto de evaluación, es decir, un proveedor de símbolos (SP), la dirección de ejecución actual y un objeto de enlazador. Para obtener más información, consulte [Contexto de evaluación](../../extensibility/debugger/evaluation-context.md). Si la llamada se `IDebugExpressionEvaluator::GetMethodProperty` realiza correctamente, el método devuelve un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objeto, que representa el método que contiene la dirección de ejecución actual.

 El DE llama a [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) para obtener un [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) objeto, que se filtra para devolver solo los valores locales y se enumera para generar una lista de [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) estructuras. Cada estructura contiene el nombre, el tipo y el valor de un local. El tipo y el valor se almacenan como cadenas formateadas, adecuadas para su visualización. El nombre, el tipo y el valor se muestran normalmente juntos en una línea de la ventana **Locales.**

> [!NOTE]
> Las ventanas **Inspección rápida** y **Inspección** también muestran variables con el mismo formato de nombre, valor y tipo. Sin embargo, esos valores se obtienen `IDebugProperty2::EnumChildren`llamando a [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) en lugar de .

## <a name="in-this-section"></a>En esta sección
 [Ejemplo de implementación de locales](../../extensibility/debugger/sample-implementation-of-locals.md) Utiliza ejemplos para recorrer paso a paso el proceso de implementación de locales.

## <a name="related-sections"></a>Secciones relacionadas
 [Contexto de evaluación](../../extensibility/debugger/evaluation-context.md) Explica que cuando el motor de depuración (DE) llama al evaluador de expresiones (EE), pasa tres argumentos.

## <a name="see-also"></a>Vea también
 [Escribir un evaluador de expresiones CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
