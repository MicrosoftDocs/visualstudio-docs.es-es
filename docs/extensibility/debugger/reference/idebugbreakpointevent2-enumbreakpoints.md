---
title: 'IDebugBreakpointEvent2:: EnumBreakpoints | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointEvent2:::EnumBreakpoints
helpviewer_keywords:
- IDebugBreakpointEvent2:::EnumBreakpoints
ms.assetid: 606a9625-ee43-4e84-9a47-af9a50d2d005
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8744ec272fa121630e67f516ef1839c70b1a2d41
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80735034"
---
# <a name="idebugbreakpointevent2enumbreakpoints"></a>IDebugBreakpointEvent2::EnumBreakpoints
Crea un enumerador para todos los puntos de interrupción que se han desencadenado en la ubicación del código actual.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT EnumBreakpoints(
  IEnumDebugBoundBreakpoints2** ppEnum
);
```

```csharp
int EnumBreakpoints(
  out IEnumDebugBoundBreakpoints2 ppEnum
);
```

## <a name="parameters"></a>Parámetros
`ppEnum`\
enuncia Devuelve un objeto [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) que enumera todos los puntos de interrupción asociados a la ubicación del código actual.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 No todos los puntos de interrupción en una ubicación determinada se pueden activar en un momento determinado (por ejemplo, un punto de interrupción con una condición no se activará hasta que se cumpla esa condición).

## <a name="see-also"></a>Vea también
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
- [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)
