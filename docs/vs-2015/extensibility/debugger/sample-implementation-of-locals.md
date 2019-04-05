---
title: Ejemplo de implementación de las variables locales | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], local variables
- expression evaluation, local variables
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: af718d5fe5038a2baa62093078aaed9a3cccb14b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58996219"
---
# <a name="sample-implementation-of-locals"></a>Implementación de ejemplo de variables locales
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión del evaluador de expresiones Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Presentamos una visión general de cómo Visual Studio obtiene a las variables locales para un método desde el evaluador de expresiones (EE):  
  
1.  Visual Studio llama el motor de depuración (DE) [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) para obtener un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objeto que representa todas las propiedades del marco de pila, incluidas las variables locales.  
  
2.  `IDebugStackFrame2::GetDebugProperty` las llamadas [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) para obtener un objeto que describe el método dentro del cual se produjo el punto de interrupción. La DE proporciona un proveedor de símbolos ([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)), una dirección ([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)) y un enlazador ([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)).  
  
3.  `IDebugExpressionEvaluator::GetMethodProperty` las llamadas [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) con el proporcionado `IDebugAddress` objeto va a obtener un [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) que representa el método que contiene la dirección especificada.  
  
4.  El `IDebugContainerField` interfaz recibe consultas de la [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) interfaz. Es esta interfaz que proporciona acceso a variables locales del método.  
  
5.  `IDebugExpressionEvaluator::GetMethodProperty` crea una instancia de una clase (llamado `CFieldProperty` en el ejemplo) que implementa el `IDebugProperty2` interfaz para representar las variables locales del método. El `IDebugMethodField` objeto se coloca en esta `CFieldProperty` objeto junto con el `IDebugSymbolProvider`, `IDebugAddress` y `IDebugBinder` objetos.  
  
6.  Cuando el `CFieldProperty` se inicializa el objeto, [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md) se llama en el `IDebugMethodField` objeto para obtener un [FIELD_INFO](../../extensibility/debugger/reference/field-info.md) estructura que contiene toda la información que se puede mostrar sobre el propio método .  
  
7.  `IDebugExpressionEvaluator::GetMethodProperty` Devuelve el `CFieldProperty` objeto como un `IDebugProperty2` objeto.  
  
8.  Llamadas visuales Studio [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) devuelto `IDebugProperty2` objeto con el filtro `guidFilterLocalsPlusArgs`. Esto devuelve un [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) objeto que contiene variables locales del método. Esta enumeración se rellena mediante llamadas a [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) y [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md).  
  
9. Llamadas visuales Studio [siguiente](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) para obtener un [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) estructura para cada local. Esta estructura contiene un puntero a un `IDebugProperty2` interfaz para una variable local.  
  
10. Llamadas visuales Studio [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) para cada local obtener el nombre, valor y tipo de la local. Esta es la información que se muestra en el **variables locales** ventana.  
  
## <a name="in-this-section"></a>En esta sección  
 [Implementación de GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md)  
 Describe una implementación de [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md).  
  
 [Enumeración de variables locales](../../extensibility/debugger/enumerating-locals.md)  
 Describe cómo el motor de depuración (DE) realiza una llamada para enumerar las variables locales o argumentos.  
  
 [Obtención de propiedades locales](../../extensibility/debugger/getting-local-properties.md)  
 Describe cómo la DE hace una llamada para obtener el nombre, tipo y valor de uno o más variables locales.  
  
 [Obtención de valores locales](../../extensibility/debugger/getting-local-values.md)  
 Describe cómo obtener el valor de la variable local, lo que requiere los servicios de un objeto de enlazador proporcionado por el contexto de evaluación.  
  
 [Evaluación de variables locales](../../extensibility/debugger/evaluating-locals.md)  
 Explica cómo se evalúan las variables locales.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Contexto de evaluación](../../extensibility/debugger/evaluation-context.md)  
 Proporciona los argumentos que se pasan cuando llama a la del evaluador de expresiones (EE).  
  
 [Ejemplo de MyCEE](http://msdn.microsoft.com/624a018b-9179-402f-9d48-3aec87b48f4f)  
 Se muestra un enfoque de implementación a la creación de un evaluador de expresiones del lenguaje MyC.  
  
## <a name="see-also"></a>Vea también  
 [Visualización de variables locales](../../extensibility/debugger/displaying-locals.md)
