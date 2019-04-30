---
title: Visualización de variables locales | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, displaying locals
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: db7587ad6cd12c80d21caf38e7d35289e4782da3
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63411269"
---
# <a name="display-locals"></a>Variables locales de presentación
> [!IMPORTANT]
> En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [ejemplo de evaluador de expresión administrado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 La ejecución siempre tiene lugar dentro del contexto de un método, que también se conoce como el método contenedor o el método actual. Cuando la ejecución se detiene, Visual Studio llama al motor de depuración (DE) para obtener una lista de variables locales y los argumentos, se denominan a variables locales del método. Visual Studio muestra estas variables locales y sus valores en el **variables locales** ventana.

 Para mostrar las variables locales, llama la DE la [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) método perteneciente a EE y le proporciona un contexto de evaluación, que es, un proveedor de símbolos (SP), la dirección de ejecución actual y un objeto de enlazador. Para obtener más información, consulte [contexto de evaluación](../../extensibility/debugger/evaluation-context.md). Si la llamada se realiza correctamente, el `IDebugExpressionEvaluator::GetMethodProperty` método devuelve un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objeto, que representa el método que contiene la dirección de ejecución actual.

 Las llamadas DE [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) para obtener un [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) object, que se filtran para devolver solo las variables locales y enumerar para generar una lista de [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md)estructuras. Cada estructura contiene el nombre, tipo y valor de una variable local. El tipo y valor se almacenan como cadenas con formato adecuadas para su presentación. El nombre, tipo y valor normalmente se muestran juntos en una línea de la **variables locales** ventana.

> [!NOTE]
> El **Inspección rápida** y **inspección** ventanas también muestran las variables con el mismo formato de nombre, valor y tipo. Sin embargo, esos valores se obtienen mediante una llamada a [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) en lugar de `IDebugProperty2::EnumChildren`.

## <a name="in-this-section"></a>En esta sección
 [Implementación de ejemplo de variables locales](../../extensibility/debugger/sample-implementation-of-locals.md) usa ejemplos paso a paso a través del proceso de implementación de las variables locales.

## <a name="related-sections"></a>Secciones relacionadas
 [Contexto de evaluación](../../extensibility/debugger/evaluation-context.md) explica que, cuando el motor de depuración (DE) llama el evaluador de expresiones (EE), pasa tres argumentos.

## <a name="see-also"></a>Vea también
 [Escribir un evaluador de expresiones CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)