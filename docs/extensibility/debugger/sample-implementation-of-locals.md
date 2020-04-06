---
title: Ejemplo de implementación de locales ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], local variables
- expression evaluation, local variables
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6b70e0f9091d40ed6b5fc44934606f42ccd84b21
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713075"
---
# <a name="sample-implementation-of-locals"></a>Ejemplo de implementación de locales
> [!IMPORTANT]
> En Visual Studio 2015, esta forma de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, vea Evaluadores de [expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y Ejemplo de evaluador de [expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 A continuación se muestra información general sobre cómo Visual Studio obtiene los locales de un método del evaluador de expresiones (EE):

1. Visual Studio llama a [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) del motor de depuración (DE) para obtener un [Objeto IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) que representa todas las propiedades del marco de pila, incluidos los locales.

2. `IDebugStackFrame2::GetDebugProperty`llama a [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) para obtener un objeto que describe el método dentro del cual se produjo el punto de interrupción. El DE proporciona un proveedor de símbolos ([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)), una dirección ([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)) y un enlazador ([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)).

3. `IDebugExpressionEvaluator::GetMethodProperty`llama a [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) con el objeto proporcionado `IDebugAddress` para obtener un [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) que representa el método que contiene la dirección especificada.

4. Se `IDebugContainerField` consulta la interfaz para el [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) interfaz. Es esta interfaz la que da acceso a los locales del método.

5. `IDebugExpressionEvaluator::GetMethodProperty`crea una instancia `CFieldProperty` de una clase (llamada en el ejemplo) que ejecuta la `IDebugProperty2` interfaz para representar los locales del método. El `IDebugMethodField` objeto se `CFieldProperty` coloca en `IDebugSymbolProvider`este `IDebugAddress`objeto `IDebugBinder` junto con los objetos , , y .

6. Cuando `CFieldProperty` se inicializa el objeto, [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md) se llama en el `IDebugMethodField` objeto para obtener un [FIELD_INFO](../../extensibility/debugger/reference/field-info.md) estructura que contiene toda la información que se puede mostrar sobre el propio método.

7. `IDebugExpressionEvaluator::GetMethodProperty`devuelve `CFieldProperty` el objeto `IDebugProperty2` como un objeto.

8. Visual Studio llama a [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) en el objeto devuelto `IDebugProperty2` con el filtro `guidFilterLocalsPlusArgs`, que devuelve un [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) objeto que contiene los locales del método. Esta enumeración se rellena mediante llamadas a [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) y [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md).

9. Visual Studio llama a [Next](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) para obtener una estructura [de DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) para cada local. Esta estructura contiene un `IDebugProperty2` puntero a una interfaz para un local.

10. Visual Studio llama a [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) para cada local para obtener el nombre, el valor y el tipo del local. Esta información se muestra en la ventana **Locales.**

## <a name="in-this-section"></a>En esta sección
 [Implementar GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md) Describe una implementación de [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md).

 [Enumerar locales](../../extensibility/debugger/enumerating-locals.md) Describe cómo el motor de depuración (DE) realiza una llamada para enumerar variables o argumentos locales.

 [Obtener propiedades locales](../../extensibility/debugger/getting-local-properties.md) Describe cómo la DE realiza una llamada para obtener el nombre, el tipo y el valor de uno o varios locales.

 [Obtener valores locales](../../extensibility/debugger/getting-local-values.md) Describe cómo obtener el valor de local, que requiere los servicios de un objeto de enlazador proporcionado por el contexto de evaluación.

 [Evaluar a los lugareños](../../extensibility/debugger/evaluating-locals.md) Explica cómo se evalúan los locales.

## <a name="related-sections"></a>Secciones relacionadas
 [Contexto de evaluación](../../extensibility/debugger/evaluation-context.md) Proporciona los argumentos que se pasan cuando la DE llama al evaluador de expresiones (EE).

 [Muestra MyCEE](https://msdn.microsoft.com/library/624a018b-9179-402f-9d48-3aec87b48f4f) Muestra un enfoque de implementación para crear un evaluador de expresiones para el lenguaje MyC.

## <a name="see-also"></a>Vea también
- [Mostrando locales](../../extensibility/debugger/displaying-locals.md)
