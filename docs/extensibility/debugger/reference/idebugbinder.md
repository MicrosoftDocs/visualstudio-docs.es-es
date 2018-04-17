---
title: IDebugBinder | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBinder
helpviewer_keywords:
- IDebugBinder interface
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3514d280b6718fc670f3bdac35b6bbacbbf2b09c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugbinder"></a>IDebugBinder
> [!IMPORTANT]
>  Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información acerca de cómo implementar los evaluadores de expresión de CLR, vea [evaluadores de expresión de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión evaluador Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Esta interfaz enlaza a un campo de símbolo, suelen ser devuelto por el proveedor de símbolos para un contexto de memoria o un objeto que contiene el valor actual del símbolo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugBinder : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Esta interfaz es compatible con la evaluación de expresiones y debe ser implementada por el motor de depuración (Alemania).  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Esta interfaz se usa en el proceso de evaluación de la expresión y se utiliza normalmente en la implementación de [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) y [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md).  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugBinder`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Enlazar](../../../extensibility/debugger/reference/idebugbinder-bind.md)|Obtiene el contexto de la memoria o un objeto que contiene el valor actual del símbolo.|  
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|Determina el tipo de tiempo de ejecución de un objeto.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|Convierte una dirección de memoria o la ubicación del objeto en un contexto de la memoria.|  
|[GetFunctionObject](../../../extensibility/debugger/reference/idebugbinder-getfunctionobject.md)|Obtiene un [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) objeto utilizado para crear parámetros de función.|  
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|Obtiene el tipo exacto de una variable.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz devuelve los objetos que se usan por el evaluador de expresiones en árboles de análisis. El evaluador de expresiones analiza una expresión mediante el proveedor de símbolos para convertir los símbolos de la expresión en instancias de [IDebugField](../../../extensibility/debugger/reference/idebugfield.md), que describen cada símbolo en cuanto a su tipo y ubicación en el código fuente. El [enlazar](../../../extensibility/debugger/reference/idebugbinder-bind.md) método convierte `IDebugField` objetos a [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objetos que se conectan o enlazar un símbolo de tipo para un valor real en la memoria. Estos `IDebugObject` objetos, a continuación, se almacenan en un árbol de análisis para evaluarlos posteriormente.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de evaluación de expresión](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)