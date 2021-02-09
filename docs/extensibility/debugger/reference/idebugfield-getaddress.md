---
title: 'IDebugField:: GetAddress | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetAddress
helpviewer_keywords:
- IDebugField::GetAddress method
ms.assetid: 6981bf03-66ef-4bf9-87ea-f6c9624486cb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5939f0ffd3a975c5fd3286045573fbf0da8006e3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99915436"
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
enuncia Devuelve la dirección como un objeto [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
