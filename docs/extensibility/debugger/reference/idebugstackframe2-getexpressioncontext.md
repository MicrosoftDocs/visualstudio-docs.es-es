---
title: "IDebugStackFrame2::GetExpressionContext | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugStackFrame2::GetExpressionContext"
helpviewer_keywords: 
  - "IDebugStackFrame2::GetExpressionContext"
ms.assetid: a2604e6a-502d-473b-868f-b11ac64c7a35
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugStackFrame2::GetExpressionContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene un contexto de evaluación para la evaluación de expresiones en el contexto actual de un marco de pila y un subproceso.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetExpressionContext (   
   IDebugExpressionContext2** ppExprCxt  
);  
```  
  
```c#  
int GetExpressionContext (   
   out IDebugExpressionContext2 ppExprCxt  
);  
```  
  
#### Parámetros  
 `ppExprCxt`  
 \[out\]  Devuelve un objeto de [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) que representa un contexto para la evaluación de la expresión.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Normalmente, un contexto de evaluación de la expresión se puede considerar como el ámbito para realizar la evaluación de la expresión.  Llame al método de [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) para analizar una expresión y después llamar a los métodos resultantes de [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o de [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) para evaluar la expresión analizada.  
  
## Vea también  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)