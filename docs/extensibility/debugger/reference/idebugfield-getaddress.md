---
description: Este método obtiene la dirección de depuración de un campo.
title: 'IDebugField:: GetAddress | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetAddress
helpviewer_keywords:
- IDebugField::GetAddress method
ms.assetid: 6981bf03-66ef-4bf9-87ea-f6c9624486cb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 06b6d1770e5fa4c4d2548e0551c437b04e91feb2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077127"
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

## <a name="see-also"></a>Consulte también
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
