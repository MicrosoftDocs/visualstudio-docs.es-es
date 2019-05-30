---
title: IDebugCanStopEvent2::GetReason | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e1b219973e0fced92a588a87ed472cf7a57d312d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337272"
---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
Obtiene el motivo por el motor de depuración (DE) desea detener.

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

## <a name="parameters"></a>Parámetros
`pcr`\
[out] Devuelve un valor de la [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) enumeración que describe el motivo de este evento.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Normalmente, se llama a este método antes de la [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) método para que el llamador pueda determinar si se debe pasar distinto de cero (`TRUE`) a la `IDebugCanStopEvent2::CanStop` método.

 Puede ser el motivo para detener `CANSTOP_ENTRYPOINT`, lo que significa que la DE ha alcanzado un punto de entrada, o `CANSTOP_STEPIN`, lo que significa que la DE ha entrado en una función.

## <a name="see-also"></a>Vea también
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)
- [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)