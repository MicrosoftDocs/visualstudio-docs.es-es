---
title: 'IDebugCanStopEvent2:: GetReason (| Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 707488abed004adaa75c84f16358bdd8a979eb71
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191154"
---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtiene el motivo por el que el motor DE depuración (DE) desea detenerse.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 enuncia Devuelve un valor de la enumeración [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) que describe el motivo de este evento.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Observaciones  
 Normalmente, se llama a este método antes que al método [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) para que el llamador pueda determinar si pasar a un método distinto de cero ( `TRUE` ) `IDebugCanStopEvent2::CanStop` .  
  
 El motivo de la detención puede ser `CANSTOP_ENTRYPOINT` , lo que significa que el de ha alcanzado un punto de entrada, o `CANSTOP_STEPIN` , lo que significa que el de ha escalonado en una función.  
  
## <a name="see-also"></a>Consulte también  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)   
 [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)
