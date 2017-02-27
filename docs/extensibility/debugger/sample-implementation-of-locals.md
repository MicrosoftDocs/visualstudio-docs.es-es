---
title: "Implementaci&#243;n de ejemplo de variables locales | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "depurar [SDK de depuración], de variables locales"
  - "evaluación de expresiones, variables locales"
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Implementaci&#243;n de ejemplo de variables locales
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está obsoleta. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [ejemplo de evaluador de expresiones administrado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Presentamos una visión general de cómo Visual Studio obtiene a las variables locales de un método en el evaluador de expresiones \(EE\):  
  
1.  Visual Studio llama el motor de depuración \(DE\) [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) para obtener un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objeto que representa todas las propiedades del marco de pila, incluidas las variables locales.  
  
2.  `IDebugStackFrame2::GetDebugProperty` llamadas [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) para obtener un objeto que describe el método en el que se produjo el punto de interrupción. La DE proporciona un proveedor de símbolos \([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)\), una dirección \([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)\) y un enlazador \([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)\).  
  
3.  `IDebugExpressionEvaluator::GetMethodProperty` llamadas [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) suministradas `IDebugAddress` va a obtener un [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) que representa el método que contiene la dirección especificada.  
  
4.  El `IDebugContainerField` interfaz se consulta el [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) interfaz. Es esta interfaz que proporciona acceso a las variables locales del método.  
  
5.  `IDebugExpressionEvaluator::GetMethodProperty` crea una instancia de una clase \(denominada `CFieldProperty` en el ejemplo\) que implementa el `IDebugProperty2` interfaz para representar las variables locales del método. El `IDebugMethodField` se ponen en este `CFieldProperty` objeto junto con el `IDebugSymbolProvider`, `IDebugAddress` y `IDebugBinder` objetos.  
  
6.  Cuando el `CFieldProperty` se inicializa el objeto, [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md) se llama en el `IDebugMethodField` objeto que se va a obtener un [FIELD\_INFO](../../extensibility/debugger/reference/field-info.md) estructura que contiene toda la información que se pueda mostrar sobre el propio método.  
  
7.  `IDebugExpressionEvaluator::GetMethodProperty` Devuelve el `CFieldProperty` de objeto como un `IDebugProperty2` objeto.  
  
8.  Llamadas visuales Studio [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) en el valor devuelto `IDebugProperty2` objeto con el filtro `guidFilterLocalsPlusArgs`. Esto devuelve un [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) objeto que contiene variables locales del método. Esta enumeración se rellena mediante llamadas a [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) y [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md).  
  
9. Llamadas visuales Studio [Siguiente](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) para obtener un [DEBUG\_PROPERTY\_INFO](../../extensibility/debugger/reference/debug-property-info.md) estructura para cada local. Esta estructura contiene un puntero a un `IDebugProperty2` interfaz para una variable local.  
  
10. Llamadas visuales Studio [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) para cada local obtener el nombre, valor y tipo de la local. Esta es la información que se muestra en el **locales** ventana.  
  
## En esta sección  
 [Implementación GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md)  
 Describe una implementación de [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md).  
  
 [Enumerar variables locales](../../extensibility/debugger/enumerating-locals.md)  
 Describe cómo el motor de depuración \(DE\) realiza una llamada para enumerar los argumentos o variables locales.  
  
 [Obtener las propiedades locales](../../extensibility/debugger/getting-local-properties.md)  
 Describe cómo la DE hace una llamada para obtener el nombre, el tipo y el valor de una o más variables locales.  
  
 [Obtención de valores locales](../../extensibility/debugger/getting-local-values.md)  
 Describe cómo obtener el valor de la variable local, que requiere que los servicios de un objeto de enlazador dado mediante el contexto de evaluación.  
  
 [Evaluar las variables locales](../../extensibility/debugger/evaluating-locals.md)  
 Explica cómo se evalúan las variables locales.  
  
## Secciones relacionadas  
 [Contexto de evaluación](../../extensibility/debugger/evaluation-context.md)  
 Proporciona los argumentos que se pasan cuando llama a la del evaluador de expresiones \(EE\).  
  
 [MyCEE Sample](http://msdn.microsoft.com/es-es/624a018b-9179-402f-9d48-3aec87b48f4f)  
 Muestra un enfoque de implementación para crear un evaluador de expresiones del lenguaje MyC.  
  
## Vea también  
 [Mostrar variables locales](../../extensibility/debugger/displaying-locals.md)