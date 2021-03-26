---
title: Mostrar variables locales | Microsoft Docs
description: Obtenga información sobre la lista de variables locales y argumentos, denominados colectivamente las variables locales del método, que se muestran cuando se detiene la ejecución.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, displaying locals
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 564b42a15e1420027b79cb5f00c70f61649ad4f9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097271"
---
# <a name="display-locals"></a>Mostrar variables locales
> [!IMPORTANT]
> En Visual Studio 2015, esta manera de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, consulte [evaluadores](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) de expresiones CLR y [ejemplo de evaluador de expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 La ejecución siempre tiene lugar dentro del contexto de un método, también conocido como el método contenedor o el método actual. Cuando la ejecución se pausa, Visual Studio llama al motor DE depuración (DE) para obtener una lista de variables locales y argumentos, denominados colectivamente las variables locales del método. Visual Studio muestra estas variables locales y sus valores en la ventana **variables locales** .

 Para mostrar variables locales, el método DE llama al método [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) perteneciente a EE y le asigna un contexto de evaluación, es decir, un proveedor de símbolos (SP), la dirección de ejecución actual y un objeto de enlazador. Para obtener más información, vea [contexto de evaluación](../../extensibility/debugger/evaluation-context.md). Si la llamada se realiza correctamente, el `IDebugExpressionEvaluator::GetMethodProperty` método devuelve un objeto [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) , que representa el método que contiene la dirección de ejecución actual.

 El método DE llama a [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) para obtener un objeto [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) , que se filtra para devolver solo variables locales y enumeradas para generar una lista de estructuras de [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) . Cada estructura contiene el nombre, el tipo y el valor de una variable local. El tipo y el valor se almacenan como cadenas con formato, que se pueden mostrar. Normalmente, el nombre, el tipo y el valor se muestran juntos en una línea de la ventana **variables locales** .

> [!NOTE]
> Las ventanas **Inspección rápida** y **inspección** también muestran variables con el mismo formato de nombre, valor y tipo. Sin embargo, esos valores se obtienen mediante una llamada a [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) en lugar de `IDebugProperty2::EnumChildren` .

## <a name="in-this-section"></a>En esta sección
 [Implementación de ejemplo de variables locales](../../extensibility/debugger/sample-implementation-of-locals.md) Usa ejemplos para recorrer paso a paso el proceso de implementación de variables locales.

## <a name="related-sections"></a>Secciones relacionadas
 [Contexto de evaluación](../../extensibility/debugger/evaluation-context.md) Explica que cuando el motor DE depuración (DE) llama al evaluador de expresiones (EE), pasa tres argumentos.

## <a name="see-also"></a>Consulte también
 [Escribir un evaluador de expresiones CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
