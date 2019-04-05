---
title: IDebugStackFrame2::GetExpressionContext | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetExpressionContext
helpviewer_keywords:
- IDebugStackFrame2::GetExpressionContext
ms.assetid: a2604e6a-502d-473b-868f-b11ac64c7a35
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7aea3543401faa1e7a6fd3ab2d3de073b5e6b3bf
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58998092"
---
# <a name="idebugstackframe2getexpressioncontext"></a>IDebugStackFrame2::GetExpressionContext
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtiene un contexto de evaluación para la evaluación de expresiones dentro del contexto actual de un marco de pila y subproceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT GetExpressionContext (   
   IDebugExpressionContext2** ppExprCxt  
);  
```  
  
```csharp  
int GetExpressionContext (   
   out IDebugExpressionContext2 ppExprCxt  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppExprCxt`  
 [out] Devuelve un [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) objeto que representa un contexto para la evaluación de expresión.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Por lo general, un contexto de evaluación de expresión puede considerarse como un ámbito para llevar a cabo la evaluación de expresiones. Llame a la [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) método para analizar una expresión y, a continuación, llamar a resultante [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) métodos para evaluar la expresión analizada.  
  
## <a name="see-also"></a>Vea también  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
