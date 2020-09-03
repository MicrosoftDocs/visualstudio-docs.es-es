---
title: 'IDebugCanStopEvent2:: CanStop | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80734591"
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
Notifica al motor DE depuración (DE) si se debe detener o no en la ubicación del código actual o simplemente continuar la ejecución.

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
de Distinto de cero ( `TRUE` ) si el de debe detenerse en la ubicación del código actual; de lo contrario, cero ( `FALSE` ).

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 El receptor de este evento normalmente llama al método [GetReason (](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) para determinar la razón por la que el de desea detener y, a continuación, llama al `IDebugCanStopEvent2::CanStop` método con la respuesta adecuada.

 Si el DE se detiene, envía un evento que describe el motivo de la detención. Normalmente hay dos eventos que se envían, un usuario o un salto de señal representado por la interfaz [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) y un evento de punto de interrupción representado por la interfaz [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) .

## <a name="see-also"></a>Vea también
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
