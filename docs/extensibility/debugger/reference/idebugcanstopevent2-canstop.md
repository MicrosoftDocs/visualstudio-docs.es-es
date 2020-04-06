---
title: IDebugCanStopEvent2::CanStop ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::CanStop
helpviewer_keywords:
- IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2915938c966bac7f842d0745c973c7d0b7033e2b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734591"
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
Notifica al motor de depuración (DE) si se detiene o no en la ubicación del código actual o simplemente continúa la ejecución.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT CanStop ( 
   BOOL fCanStop
);
```

```csharp
int CanStop ( 
   int fCanStop
);
```

## <a name="parameters"></a>Parámetros
`fCanStop`\
[en] Distinto de`TRUE`cero ( ) si el DE debe detenerse en la ubicación del código actual; de lo`FALSE`contrario, cero ( ).

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 El receptor de este evento normalmente llama a la [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) método para `IDebugCanStopEvent2::CanStop` determinar el motivo que la DE desea detener y, a continuación, llama al método con la respuesta adecuada.

 Si el DE se detiene, envía un evento que describe el motivo de la detención. Normalmente hay dos eventos que se envían, un usuario o un salto de señal representado por el [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) interfaz y un evento de punto de interrupción representado por el [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) interfaz.

## <a name="see-also"></a>Vea también
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
