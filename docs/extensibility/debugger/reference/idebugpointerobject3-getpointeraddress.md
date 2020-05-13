---
title: IDebugPointerObject3::GetPointerAddress Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetPointerAddress
- IDebugPointerObject3::GetPointerAddress
ms.assetid: 4cc5af04-9e70-420d-8230-ef3108df6d51
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9a508a5861b3b128a964be4a5c3ca7714858318c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725477"
---
# <a name="idebugpointerobject3getpointeraddress"></a>IDebugPointerObject3::GetPointerAddress
Recupera la dirección del puntero.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetPointerAddress (
   UINT64* puAddress
);
```

```csharp
int GetPointerAddress (
   out ulong puAddress
);
```

## <a name="parameters"></a>Parámetros
`puAddress`[fuera] Devuelve la dirección del puntero.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)
