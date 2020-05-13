---
title: IDebugCanStopEvent2::GetReason ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 59e611c3ed69528f92a6085cf74aa44efed09144
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734524"
---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
Obtiene la razón por la que el motor de depuración (DE) desea detenerse.

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
[fuera] Devuelve un valor de la [enumeración CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) que describe el motivo de este evento.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Normalmente se llama a este método antes del método [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) para`TRUE`que `IDebugCanStopEvent2::CanStop` el llamador pueda determinar si se debe pasar un valor distinto de cero ( ) al método.

 La razón de la `CANSTOP_ENTRYPOINT`detención puede ser , lo que `CANSTOP_STEPIN`significa que el DE ha alcanzado un punto de entrada, o , lo que significa que el DE ha entrado en una función.

## <a name="see-also"></a>Vea también
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)
- [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)
