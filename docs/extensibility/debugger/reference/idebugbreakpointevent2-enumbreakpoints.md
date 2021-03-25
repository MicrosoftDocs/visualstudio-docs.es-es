---
description: Crea un enumerador para todos los puntos de interrupción que se han desencadenado en la ubicación del código actual.
title: 'IDebugBreakpointEvent2:: EnumBreakpoints | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointEvent2:::EnumBreakpoints
helpviewer_keywords:
- IDebugBreakpointEvent2:::EnumBreakpoints
ms.assetid: 606a9625-ee43-4e84-9a47-af9a50d2d005
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ee18b1e24730b003e9b5cecaa0eac9bbdd87a913
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054509"
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

## <a name="see-also"></a>Consulte también
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
- [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)
