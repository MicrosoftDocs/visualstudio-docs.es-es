---
title: "IDebugBinder | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBinder"
helpviewer_keywords: 
  - "Interfaz IDebugBinder"
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBinder
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está obsoleta. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [ejemplo de evaluador de expresiones administrado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Esta interfaz enlaza a un campo de símbolo suelen ser devuelto por el proveedor de símbolos para un contexto de la memoria o el objeto que contiene el valor actual de.  
  
## Sintaxis  
  
```  
IDebugBinder : IUnknown  
```  
  
## Notas para los implementadores  
 Esta interfaz admite la evaluación de expresión y debe ser implementada por el motor de depuración \(DE\).  
  
## Notas para los llamadores  
 Esta interfaz se utiliza en el proceso de evaluación de la expresión y se utiliza normalmente en la implementación de [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) y [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md).  
  
## Métodos en orden de Vtable  
 La siguiente tabla muestra los métodos de `IDebugBinder`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Enlazar](../../../extensibility/debugger/reference/idebugbinder-bind.md)|Obtiene el contexto de la memoria o el objeto que contiene el valor actual del símbolo.|  
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|Determina el tipo de tiempo de ejecución de un objeto.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|Convierte una dirección de memoria o la ubicación del objeto en un contexto de la memoria.|  
|[GetFunctionObject](../../../extensibility/debugger/reference/idebugbinder-getfunctionobject.md)|Obtiene un [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) objeto utilizado para crear parámetros de función.|  
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|Obtiene el tipo exacto de una variable.|  
  
## Comentarios  
 Esta interfaz devuelve objetos que se usan por el evaluador de expresiones en árboles de análisis. El evaluador de expresiones analiza una expresión mediante el proveedor de símbolos para convertir los símbolos de la expresión en instancias de [IDebugField](../../../extensibility/debugger/reference/idebugfield.md), que describen cada símbolo en cuanto a su tipo y ubicación en el código fuente. El [Enlazar](../../../extensibility/debugger/reference/idebugbinder-bind.md) método convierte `IDebugField` objetos de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objetos que se conectan o enlazar un símbolo de tipo para un valor real en la memoria. Estos `IDebugObject` objetos se almacenan en un árbol de análisis para la evaluación posterior.  
  
## Requisitos  
 Encabezado: ee.h  
  
 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de evaluación de expresión](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)