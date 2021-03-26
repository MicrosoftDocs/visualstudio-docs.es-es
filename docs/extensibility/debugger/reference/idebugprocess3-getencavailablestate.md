---
description: Este método obtiene el estado actual de edición y continuación del proceso.
title: 'IDebugProcess3:: GetENCAvailableState | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::GetENCAvailableState
helpviewer_keywords:
- IDebugProcess3::GetENCAvailableState
ms.assetid: 98a5d527-8a72-476c-8e92-0bff3d97c195
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c851689d9e47250457c93d1621acb6c5db98732b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081560"
---
# <a name="idebugprocess3getencavailablestate"></a>IDebugProcess3::GetENCAvailableState
Este método obtiene el estado actual de edición y continuación del proceso. Un proveedor de Puerto personalizado siempre debe devolver `E_NOTIMPL` .

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetENCAvailableState(
   EncUnavailableReason* pReason
);
```

```csharp
int GetENCAvailableState(
   EncUnavailableReason[] pReason
);
```

## <a name="parameters"></a>Parámetros
`pReason`\
enuncia Un valor de la enumeración [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md) .

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve el código de error.

> [!NOTE]
> Un proveedor de Puerto personalizado siempre debe devolver `E_NOTIMPL` .

## <a name="remarks"></a>Observaciones
 Este estado puede verse afectado por [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md).

## <a name="see-also"></a>Consulte también
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)
- [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)
