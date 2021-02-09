---
title: 'IEnumDebugPropertyInfo2:: Clone | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPropertyInfo2::Clone
helpviewer_keywords:
- IEnumDebugPropertyInfo2::Clone
ms.assetid: 0ede1667-1071-4aa4-b887-260ea103d724
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c4db18a510fa80d8afef5ed4f338e1d344ad37c3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877387"
---
# <a name="ienumdebugpropertyinfo2clone"></a>IEnumDebugPropertyInfo2::Clone
Devuelve una copia de la enumeración actual como objeto independiente.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Clone(
   IEnumDebugPropertyInfo2** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugPropertyInfo2 ppEnum
);
```

## <a name="parameters"></a>Parámetros
`ppEnum`\
[out] Devuelve una copia de esta enumeración como un objeto independiente.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Notas
 La copia de la enumeración tiene el mismo estado que el original en el momento en que se llama a este método. Sin embargo, los Estados de la copia y del original son independientes y se pueden cambiar individualmente.

## <a name="see-also"></a>Vea también
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
