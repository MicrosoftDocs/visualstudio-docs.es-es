---
title: "IDebugExpression2 | Microsoft Docs"
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
  - "IDebugExpression2"
helpviewer_keywords: 
  - "Interfaz IDebugExpression2"
ms.assetid: f5e4b124-1e30-47c8-a511-80084a02dba5
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugExpression2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

esta interfaz representa una expresión analizada lista para enlazar y evaluar.  
  
## Sintaxis  
  
```  
IDebugExpression2 : IUnknown  
```  
  
## Notas para los implementadores  
 El motor de depuración \(DE\) implementa esta interfaz para representar una expresión analizada lista para evaluar.  
  
## Notas para los llamadores  
 una llamada a [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) devuelve esta interfaz.  [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) devuelve la interfaz de [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) .  Estas interfaces son accesibles únicamente cuando se ha pausado el programa que se depura y un marco de pila está disponible.  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDebugExpression2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Evalúa esta expresión de forma asincrónica.|  
|[Abort](../../../extensibility/debugger/reference/idebugexpression2-abort.md)|Finaliza la evaluación asincrónica de la expresión.|  
|[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Evalúa esta expresión sincrónicamente.|  
  
## Comentarios  
 Cuando un programa ha detenido, el administrador de depuración de sesión \(SDM\) obtiene un marco de pila de con una llamada a [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md).  El SDM llama [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) para obtener la interfaz de [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) .  Esto va seguida por una llamada a [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) para crear la interfaz de `IDebugExpression2` , que representa la expresión analizada lista para evaluar.  
  
 El SDM llama [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) para evaluar la expresión y generar realmente un valor.  
  
 En una implementación de `IDebugExpressionContext2::ParseText`, el OF utiliza la función de `CoCreateInstance` COM para crear instancias de un evaluador de expresiones y para obtener una interfaz de [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) \(vea el ejemplo de la interfaz de `IDebugExpressionEvaluator` \).  El OF llama [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) para obtener una interfaz de [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) .  Esta interfaz se utiliza en la implementación de `IDebugExpression2::EvaluateSync` y de `IDebugExpression2::EvaluateAsync` para realizar la evaluación.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)