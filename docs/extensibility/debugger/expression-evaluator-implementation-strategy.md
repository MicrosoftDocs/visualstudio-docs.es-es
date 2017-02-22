---
title: "Estrategia de implementaci&#243;n del evaluador de expresiones | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "evaluación de expresiones, estrategia de implementación"
  - "motores de depuración, estrategias de implementación"
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Estrategia de implementaci&#243;n del evaluador de expresiones
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está obsoleta. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [ejemplo de evaluador de expresiones administrado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Es un enfoque para crear rápidamente un evaluador de expresiones \(EE\) implementar el código mínimo necesario para mostrar las variables locales en el **locales** ventana. Resulta útil tener en cuenta que cada línea en el **locales** ventana muestra el nombre, tipo y valor de una variable local y que las tres se representan mediante un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objeto. El nombre, tipo y valor de una variable local pueden obtenerse una `IDebugProperty2` objeto llamando a su [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) método. Para obtener más información acerca de cómo mostrar las variables locales en el **locales** ventana, consulte [Mostrar variables locales](../../extensibility/debugger/displaying-locals.md).  
  
## Explicación  
 Inicia una secuencia de implementación posible con la implementación de [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md). El [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) y el [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) métodos deben implementarse para mostrar las variables locales. Una llamada a `IDebugExpressionEvaluator::GetMethodProperty` devuelve un `IDebugProperty2` objeto que representa un método: es decir, un [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) objeto. No se muestran los propios métodos en el **locales** ventana.  
  
 El [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) método debe implementarse a continuación. El motor de depuración \(DE\) llama a este método para obtener una lista de las variables locales y argumentos pasando `IDebugProperty2::EnumChildren` un `guidFilter` argumento de `guidFilterLocalsPlusArgs`.`IDebugProperty2::EnumChildren` llamadas [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) y [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md), combinando los resultados de una enumeración único. Vea [Mostrar variables locales](../../extensibility/debugger/displaying-locals.md) para obtener más información.  
  
## Vea también  
 [Implementar un evaluador de expresiones](../../extensibility/debugger/implementing-an-expression-evaluator.md)   
 [Mostrar variables locales](../../extensibility/debugger/displaying-locals.md)