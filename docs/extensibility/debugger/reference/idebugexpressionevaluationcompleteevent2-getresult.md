---
title: IDebugExpressionEvaluationCompleteEvent2::GetResult | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExpressionEvaluationCompleteEvent2::GetResult
helpviewer_keywords:
- IDebugExpressionEvaluationCompleteEvent2::GetResult
ms.assetid: d9ad3e22-b6b2-421e-9a43-6bb8c70d12a9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 92496965fe463df4343d51b07819c073de163368
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugexpressionevaluationcompleteevent2getresult"></a>IDebugExpressionEvaluationCompleteEvent2::GetResult
Obtiene el resultado de evaluación de expresión.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetResult(   
   IDebugProperty2** ppResult  
);  
```  
  
```csharp  
int GetResult(   
   out IDebugProperty2 ppResult  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppResult`  
 [out] Devuelve un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) objeto que representa el resultado de la evaluación de expresiones.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 El valor devuelto [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) objeto contiene el valor de la expresión evaluada. Tenga en cuenta que este valor puede ser un valor complejo, como una matriz, pero el resultado final debe ser un numérico o valor de cadena que se muestra al usuario.  
  
## <a name="see-also"></a>Vea también  
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)