---
title: Ejemplo de implementación de variables locales | Microsoft Docs
description: Obtenga información sobre cómo obtiene Visual Studio las variables locales para un método del evaluador de expresiones de este artículo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: sample
helpviewer_keywords:
- debugging [Debugging SDK], local variables
- expression evaluation, local variables
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ac52f1524c4be2e4a7afcbd21fb437977fb663e3
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902285"
---
# <a name="sample-implementation-of-locals"></a>Implementación de ejemplo de variables locales
> [!IMPORTANT]
> En Visual Studio 2015, esta forma de implementar evaluadores de expresiones está en desuso. Para obtener información sobre cómo implementar evaluadores de expresiones CLR, vea [Evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Ejemplo de evaluador de expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 A continuación se muestra información general sobre cómo obtiene Visual Studio las variables locales para un método del evaluador de expresiones (EE):

1. Visual Studio llama a [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) del motor de depuración (DE) para obtener un objeto [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) que representa todas las propiedades del marco de pila, incluidas las variables locales.

2. `IDebugStackFrame2::GetDebugProperty` llama a [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) para obtener un objeto que describe el método en el que se ha producido el punto de interrupción. El DE proporciona un proveedor de símbolos ([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)), una dirección ([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)) y un enlazador ([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)).

3. `IDebugExpressionEvaluator::GetMethodProperty` llama a [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) con el objeto `IDebugAddress` proporcionado para obtener un objeto [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) que representa el método que contiene la dirección especificada.

4. Se consulta la interfaz [IDebugMethodField.](../../extensibility/debugger/reference/idebugmethodfield.md) en la interfaz `IDebugContainerField`. Esta interfaz es la que proporciona acceso a las variables locales del método.

5. `IDebugExpressionEvaluator::GetMethodProperty` crea una instancia de una clase (`CFieldProperty` en el ejemplo) que ejecuta la interfaz `IDebugProperty2` para representar las variables locales del método. El objeto `IDebugMethodField` se coloca en este objeto `CFieldProperty` junto con los objetos `IDebugSymbolProvider`, `IDebugAddress` y `IDebugBinder`.

6. Cuando se inicializa el objeto `CFieldProperty`, se llama a [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md) en el objeto `IDebugMethodField` para obtener una estructura [FIELD_INFO](../../extensibility/debugger/reference/field-info.md) que contiene toda la información que se puede mostrar sobre el propio método.

7. `IDebugExpressionEvaluator::GetMethodProperty` devuelve el objeto `CFieldProperty` como un objeto `IDebugProperty2`.

8. Visual Studio llama a [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) en el objeto `IDebugProperty2` devuelto con el filtro `guidFilterLocalsPlusArgs`, que devuelve un objeto [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) que contiene las variables locales del método. Esta enumeración se rellena mediante llamadas a [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) y [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md).

9. Visual Studio llama a [Next](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) para obtener una estructura [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) para cada variable local. Esta estructura contiene un puntero a una interfaz `IDebugProperty2` para una variable local.

10. Visual Studio llama a [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) en cada variable local para obtener su nombre, valor y tipo. Esta información se muestra en la ventana **Variables locales**.

## <a name="in-this-section"></a>En esta sección
 [Implementación de GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md) Se describe una implementación de [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md).

 [Enumeración de variables locales](../../extensibility/debugger/enumerating-locals.md) Se describe cómo el motor de depuración (DE) realiza una llamada para enumerar variables locales o argumentos.

 [Obtención de propiedades de variables locales](../../extensibility/debugger/getting-local-properties.md) Se describe cómo el DE realiza una llamada para obtener el nombre, el tipo y el valor de una variable local o varias.

 [Obtención de valores de variables locales](../../extensibility/debugger/getting-local-values.md) Se describe cómo obtener el valor de la variable local, para lo que se necesitan los servicios de un objeto enlazador proporcionado por el contexto de evaluación.

 [Evaluación de variables locales](../../extensibility/debugger/evaluating-locals.md) Se explica cómo se evalúan las variables locales.

## <a name="related-sections"></a>Secciones relacionadas
 [Contexto de evaluación](../../extensibility/debugger/evaluation-context.md) Proporciona los argumentos que se pasan cuando el DE llama al evaluador de expresiones (EE).

 [Ejemplo de MyCEE](/previous-versions/) Se muestra un enfoque de implementación para crear un evaluador de expresiones para el lenguaje MyC.

## <a name="see-also"></a>Consulta también
- [Visualización de variables locales](../../extensibility/debugger/displaying-locals.md)