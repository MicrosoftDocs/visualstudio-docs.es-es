---
title: "Mostrar variables locales | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "depurar [SDK de depuración], la evaluación de expresiones"
  - "evaluación de expresiones, Mostrar variables locales"
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Mostrar variables locales
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está obsoleta. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [ejemplo de evaluador de expresiones administrado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Ejecución siempre tiene lugar dentro del contexto de un método, también conocido como el método contenedor o el método actual. Cuando la ejecución se detiene, Visual Studio llama al motor de depuración \(DE\) para obtener una lista de variables locales y argumentos, que se denominan colectivamente las variables locales del método. Visual Studio muestra estas variables locales y sus valores en el **locales** ventana.  
  
 Para mostrar las variables locales, llama a la DE la [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) método perteneciente a EE y le proporciona un contexto de evaluación, que es, un proveedor de símbolos \(SP\), la dirección de ejecución actual y un objeto de enlazador. Para obtener más información, consulta [Contexto de evaluación](../../extensibility/debugger/evaluation-context.md). Si la llamada se realiza correctamente, el `IDebugExpressionEvaluator::GetMethodProperty` método devuelve un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objeto, que representa el método que contiene la dirección de ejecución actual.  
  
 Las llamadas DE [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) para obtener un [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) object, que se filtran para devolver sólo locales y enumerar para generar una lista de [DEBUG\_PROPERTY\_INFO](../../extensibility/debugger/reference/debug-property-info.md) estructuras. Cada estructura contiene el nombre, tipo y valor de una variable local. El tipo y valor se almacenan como cadenas con formato adecuadas para su presentación. El nombre, tipo y valor normalmente se muestran juntos en una línea de la **locales** ventana.  
  
> [!NOTE]
>  El **Inspección rápida** y **inspección** windows también Mostrar variables con el mismo formato de nombre, valor y tipo. Sin embargo, esos valores se obtienen llamando a [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) en lugar de `IDebugProperty2::EnumChildren`.  
  
## En esta sección  
 [Implementación de ejemplo de variables locales](../../extensibility/debugger/sample-implementation-of-locals.md)  
 Utiliza ejemplos paso a paso a través del proceso de implementación de variables locales.  
  
## Secciones relacionadas  
 [Contexto de evaluación](../../extensibility/debugger/evaluation-context.md)  
 Explica que, cuando el motor de depuración \(DE\) llama el evaluador de expresiones \(EE\), pasa tres argumentos.  
  
## Vea también  
 [Escribir un evaluador de expresiones de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)