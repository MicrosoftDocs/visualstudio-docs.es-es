---
title: Ejemplo de implementación de variables locales | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], local variables
- expression evaluation, local variables
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 56ac92989abe929884ac029e3b9c9c7dafad5fd9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="sample-implementation-of-locals"></a>Implementación de ejemplo de variables locales
> [!IMPORTANT]
>  Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información acerca de cómo implementar los evaluadores de expresión de CLR, vea [evaluadores de expresión de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión evaluador Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Presentamos una introducción acerca del modo en que Visual Studio obtiene a las variables locales para un método en el evaluador de expresiones (EE):  
  
1.  Visual Studio llama el motor de depuración (Alemania) [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) para obtener un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objeto que representa todas las propiedades del marco de pila, incluidas las variables locales.  
  
2.  `IDebugStackFrame2::GetDebugProperty` llamadas [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) para obtener un objeto que describe el método en el que se produjo el punto de interrupción. La DE proporciona un proveedor de símbolos ([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)), una dirección ([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)) y un enlazador ([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)).  
  
3.  `IDebugExpressionEvaluator::GetMethodProperty` llamadas [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) con proporcionado `IDebugAddress` objeto que se va a obtener un [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) que representa el método que contiene la dirección especificada.  
  
4.  El `IDebugContainerField` interfaz recibe consultas de la [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) interfaz. Es esta interfaz que proporciona acceso a las variables locales del método.  
  
5.  `IDebugExpressionEvaluator::GetMethodProperty` crea una instancia de una clase (denominado `CFieldProperty` en el ejemplo) que implementa el `IDebugProperty2` interfaz para representar las variables locales del método. El `IDebugMethodField` objeto se coloca en esta `CFieldProperty` objeto junto con el `IDebugSymbolProvider`, `IDebugAddress` y `IDebugBinder` objetos.  
  
6.  Cuando el `CFieldProperty` se inicializa el objeto, [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md) se llama en el `IDebugMethodField` objeto que se va a obtener un [FIELD_INFO](../../extensibility/debugger/reference/field-info.md) estructura que contiene toda la información que se pueden mostrar sobre el propio método .  
  
7.  `IDebugExpressionEvaluator::GetMethodProperty` Devuelve el `CFieldProperty` objeto como un `IDebugProperty2` objeto.  
  
8.  Llamadas visuales Studio [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) en el valor devuelto `IDebugProperty2` objeto con el filtro `guidFilterLocalsPlusArgs`. Esto devuelve un [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) objeto que contiene variables locales del método. Esta enumeración se rellena mediante llamadas a [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) y [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md).  
  
9. Llamadas visuales Studio [siguiente](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) para obtener un [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) estructura para cada local. Esta estructura contiene un puntero a un `IDebugProperty2` interfaz para una variable local.  
  
10. Llamadas visuales Studio [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) para cada local obtener el nombre, el valor y el tipo de la local. Esta es la información que se muestra en el **locales** ventana.  
  
## <a name="in-this-section"></a>En esta sección  
 [Implementación de GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md)  
 Describe una implementación de [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md).  
  
 [Enumeración de variables locales](../../extensibility/debugger/enumerating-locals.md)  
 Describe cómo el motor de depuración (Alemania) realiza una llamada para enumerar las variables locales o argumentos.  
  
 [Obtención de propiedades locales](../../extensibility/debugger/getting-local-properties.md)  
 Describe cómo el Alemania realiza una llamada para obtener el nombre, el tipo y el valor de uno o más variables locales.  
  
 [Obtención de valores locales](../../extensibility/debugger/getting-local-values.md)  
 Describe cómo obtener el valor de la variable local, que requiere que los servicios de un objeto de enlazador proporcionado por el contexto de evaluación.  
  
 [Evaluación de variables locales](../../extensibility/debugger/evaluating-locals.md)  
 Explica cómo se evalúan las variables locales.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Contexto de evaluación](../../extensibility/debugger/evaluation-context.md)  
 Proporciona los argumentos que se pasan cuando llama a la del evaluador de expresiones (EE).  
  
 [Ejemplo de MyCEE](http://msdn.microsoft.com/en-us/624a018b-9179-402f-9d48-3aec87b48f4f)  
 Muestra un enfoque de implementación a la creación de un evaluador de expresiones del lenguaje MyC.  
  
## <a name="see-also"></a>Vea también  
 [Visualización de variables locales](../../extensibility/debugger/displaying-locals.md)