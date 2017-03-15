---
title: "IDebugExpressionEvaluationCompleteEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpressionEvaluationCompleteEvent2"
helpviewer_keywords: 
  - "IDebugExpressionEvaluationCompleteEvent2"
ms.assetid: d538fc19-55bf-4231-9595-eb01e84fd1d8
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugExpressionEvaluationCompleteEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz es enviada por el motor de depuración \(DE\) al administrador de depuración de la sesión \(SDM\) cuando se completa la evaluación asincrónica de la expresión.  
  
## Sintaxis  
  
```  
IDebugExpressionEvaluationCompleteEvent2 : IUnknown  
```  
  
## Notas para los implementadores  
 El OF implementa esta interfaz para notificar la finalización de una evaluación de la expresión iniciada por una llamada a [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md).  la interfaz de [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) se debe implementar en el mismo objeto que esta interfaz.  El SDM utiliza [QueryInterface](/visual-cpp/atl/queryinterface) para tener acceso a la interfaz de `IDebugEvent2` .  
  
## Notas para los llamadores  
 El OF crea y envía este objeto event para notificar la finalización de una evaluación de la expresión.  El evento se envía mediante la función de devolución de llamada de [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) proporcionada por el SDM cuando adjuntó el programa que se depura.  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDebugExpressionEvaluationCompleteEvent2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)|obtiene la expresión original.|  
|[GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)|obtiene el resultado de la evaluación de la expresión.|  
  
## Comentarios  
 El OF debe enviar este evento, si la evaluación estaba correctamente o no.  
  
 Si la evaluación no se realizó correctamente, los indicadores de `DEBUG_PROPINFO_VALUE` y de `DEBUG_PROPINFO_ATTRIB` no estarán establecidos en la estructura de [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) devuelta por [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) \(objeto de [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) crea el OF y devuelto en el evento de `IDebugExpressionEvaluationCompleteEvent2` si se produjo un error en la evaluación\).  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)