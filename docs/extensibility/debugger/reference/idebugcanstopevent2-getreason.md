---
title: IDebugCanStopEvent2::GetReason | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4c0eaefee714467084898182b338ceda63ebdc0f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
Obtiene el motivo por qué el motor de depuración (Alemania) desea detener.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetReason(   
   CANSTOP_REASON* pcr  
);  
```  
  
```csharp  
int GetReason(   
   out enum_CANSTOP_REASON pcr  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pcr`  
 [out] Devuelve un valor de la [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) enumeración que describe el motivo de este evento.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Normalmente se llama a este método antes de la [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) método para el llamador pueda determinar si se debe pasar distinto de cero (`TRUE`) a la `IDebugCanStopEvent2::CanStop` método.  
  
 La razón de detención puede ser `CANSTOP_ENTRYPOINT`, lo que significa que la DE ha alcanzado un punto de entrada, o `CANSTOP_STEPIN`, lo que significa que la DE ha aumentado a una función.  
  
## <a name="see-also"></a>Vea también  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)   
 [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)