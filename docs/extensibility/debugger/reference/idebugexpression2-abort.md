---
title: IDebugExpression2::Abort | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExpression2::Abort
helpviewer_keywords:
- IDebugExpression2::Abort
ms.assetid: 4fcb712e-1bdb-4b75-a440-35cc79ee147e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5f4809fcf8e6947309182ff595ad2784b873f529
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugexpression2abort"></a>IDebugExpression2::Abort
Este método cancela de evaluación de expresiones asincrónica como iniciado mediante una llamada a la [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) método.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT Abort(  
   void  
);  
```  
  
```csharp  
int Abort();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Cuando se cancela la evaluación de expresiones en asincrónico, no envía una [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) eventos a la devolución de llamada de evento que se pasan a la [adjuntar](../../../extensibility/debugger/reference/idebugprogram2-attach.md) o [adjuntar](../../../extensibility/debugger/reference/idebugengine2-attach.md) métodos.  
  
## <a name="see-also"></a>Vea también  
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)