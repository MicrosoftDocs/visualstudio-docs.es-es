---
title: 'IEnumCodePaths2:: GetCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCodePaths2::GetCount
helpviewer_keywords:
- IEnumCodePaths2::GetCount
ms.assetid: 988c5092-fcc5-43a1-a94c-c261edd56ebf
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b85490c3641158ecff6881e139dbec54796e0f5a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912927"
---
# <a name="ienumcodepaths2getcount"></a>IEnumCodePaths2::GetCount
Devuelve el número de elementos de la enumeración.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetCount(
   ULONG* pcelt
);
```

```csharp
int GetCount(
   out uint pcelt
);
```

## <a name="parameters"></a>Parámetros
`pcelt`\
enuncia Devuelve el número de elementos de la enumeración.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Notas
 Este método no forma parte de la interfaz de enumeración com personalizada, que especifica que `Next` solo `Clone` `Skip` `Reset` se deben implementar los métodos,, y.

## <a name="see-also"></a>Vea también
- [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)
