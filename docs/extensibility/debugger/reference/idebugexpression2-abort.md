---
title: IDebugExpression2::Abort | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugExpression2::Abort
helpviewer_keywords: IDebugExpression2::Abort
ms.assetid: 4fcb712e-1bdb-4b75-a440-35cc79ee147e
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 94cbeaa3231f06d70d8e9f70193ccb48cbd49b5a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
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