---
title: 'IEnumDebugAddresses:: RESET | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses::Reset
helpviewer_keywords:
- IEnumDebugAddresses::Reset method
ms.assetid: 3a9d7f20-5bc6-4e13-8e91-5af4092e092f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a29620fe97079c865aa18d354a88cc6bd12e6893
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897091"
---
# <a name="ienumdebugaddressesreset"></a>IEnumDebugAddresses::Reset
Este método restablece la enumeración al primer elemento.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Reset(void);
```

```csharp
int Reset();
```

## <a name="parameters"></a>Parámetros
 None

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Notas
 Después de llamar a este método, la siguiente llamada a [Next](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md) devuelve el primer elemento de la enumeración.

## <a name="see-also"></a>Vea también
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
- [Siguiente](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)
