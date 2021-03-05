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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 13ad3bc88ab1e9f10dc87db7d7124adc993b168c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149786"
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
