---
title: 'IEnumDebugFields:: RESET | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields::Reset
helpviewer_keywords:
- IEnumDebugFields::Reset method
ms.assetid: 38ff61e4-0120-42e8-971a-16be6050b425
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1cbe3ecaf681a0fb88dab46b9c2dac2110b7beb4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919681"
---
# <a name="ienumdebugfieldsreset"></a>IEnumDebugFields::Reset
Este método restablece la enumeración al primer elemento.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Reset(void);
```

```csharp
int Reset();
```

#### <a name="parameters"></a>Parámetros
 None

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Notas
 Después de llamar a este método, la siguiente llamada a [Next](../../../extensibility/debugger/reference/ienumdebugfields-next.md) devuelve el primer elemento de la enumeración.

## <a name="see-also"></a>Vea también
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [Siguiente](../../../extensibility/debugger/reference/ienumdebugfields-next.md)
