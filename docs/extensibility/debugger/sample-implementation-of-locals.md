---
title: Ejemplo de implementación de las variables locales | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], local variables
- expression evaluation, local variables
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 17de5858870afe3064f57cb51ec8b713bb65ddf9
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60047650"
---
# <a name="sample-implementation-of-locals"></a>Implementación de ejemplo de variables locales
> [!IMPORTANT]
>  En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [ejemplo de evaluador de expresión administrado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Es una visión general de cómo Visual Studio obtiene a las variables locales de un método desde el evaluador de expresiones (EE):

1. Visual Studio llama el motor de depuración (DE) [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) para obtener un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objeto que representa todas las propiedades del marco de pila, incluidas las variables locales.

2. `IDebugStackFrame2::GetDebugProperty` las llamadas [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) para obtener un objeto que describe el método dentro del cual se produjo el punto de interrupción. La DE proporciona un proveedor de símbolos ([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)), una dirección ([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)) y un enlazador ([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)).

3. `IDebugExpressionEvaluator::GetMethodProperty` las llamadas [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) con el proporcionado `IDebugAddress` objeto va a obtener un [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) que representa el método que contiene la dirección especificada.

4. El `IDebugContainerField` interfaz recibe consultas de la [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) interfaz. Es esta interfaz que proporciona acceso a variables locales del método.

5. `IDebugExpressionEvaluator::GetMethodProperty` crea una instancia de una clase (llamado `CFieldProperty` en el ejemplo) que se ejecuta el `IDebugProperty2` interfaz para representar las variables locales del método. El `IDebugMethodField` objeto se coloca en esta `CFieldProperty` objeto junto con el `IDebugSymbolProvider`, `IDebugAddress`, y `IDebugBinder` objetos.

6. Cuando el `CFieldProperty` se inicializa el objeto, [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md) se llama en el `IDebugMethodField` objeto va a obtener un [FIELD_INFO](../../extensibility/debugger/reference/field-info.md) estructura que contiene toda la información que se puede mostrar sobre el propio método.

7. `IDebugExpressionEvaluator::GetMethodProperty` Devuelve el `CFieldProperty` objeto como un `IDebugProperty2` objeto.

8. Llamadas visuales Studio [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) devuelto `IDebugProperty2` objeto con el filtro `guidFilterLocalsPlusArgs`, que devuelve un [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) objeto que contiene variables locales del método. Esta enumeración se rellena mediante llamadas a [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) y [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md).

9. Llamadas visuales Studio [siguiente](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) para obtener un [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) estructura para cada local. Esta estructura contiene un puntero a un `IDebugProperty2` interfaz para una variable local.

10. Llamadas visuales Studio [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) para cada local obtener el nombre, valor y tipo de la local. Esta información se muestra en el **variables locales** ventana.

## <a name="in-this-section"></a>En esta sección
 [Implementar GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md) describe una implementación de [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md).

 [Enumerar variables locales](../../extensibility/debugger/enumerating-locals.md) describe cómo el motor de depuración (DE) realiza una llamada para enumerar las variables locales o argumentos.

 [Obtener propiedades locales](../../extensibility/debugger/getting-local-properties.md) describe cómo pone a la DE una llamada para obtener el nombre, tipo y valor de uno o más variables locales.

 [Obtener valores locales](../../extensibility/debugger/getting-local-values.md) trata de obtener el valor de la variable local, lo que requiere los servicios de un objeto de enlazador proporcionado por el contexto de evaluación.

 [Evaluar las variables locales](../../extensibility/debugger/evaluating-locals.md) explica cómo se evalúan las variables locales.

## <a name="related-sections"></a>Secciones relacionadas
 [Contexto de evaluación](../../extensibility/debugger/evaluation-context.md) proporciona los argumentos que se pasan cuando llama a la del evaluador de expresiones (EE).

 [Ejemplo de MyCEE](https://msdn.microsoft.com/library/624a018b-9179-402f-9d48-3aec87b48f4f) muestra un enfoque de implementación a la creación de un evaluador de expresiones del lenguaje MyC.

## <a name="see-also"></a>Vea también
- [Visualización de variables locales](../../extensibility/debugger/displaying-locals.md)