---
title: IDebugField::GetAddress ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetAddress
helpviewer_keywords:
- IDebugField::GetAddress method
ms.assetid: 6981bf03-66ef-4bf9-87ea-f6c9624486cb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1be3d839cabe3fce07cdd42720306bdac47282f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729006"
---
# <a name="idebugfieldgetaddress"></a>IDebugField::GetAddress
Este método obtiene la dirección de depuración de un campo.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetAddress( 
   IDebugAddress** ppAddress
);
```

```csharp
int GetAddress(
   out IDebugAddress ppAddress
);
```

## <a name="parameters"></a>Parámetros
`ppAddress`\
[fuera] Devuelve la dirección como un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) objeto.

## <a name="return-value"></a>Valor devuelto
 Si se `S_OK`realiza correctamente, devuelve ; de lo contrario, devuelva un código de error.

## <a name="see-also"></a>Vea también
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
