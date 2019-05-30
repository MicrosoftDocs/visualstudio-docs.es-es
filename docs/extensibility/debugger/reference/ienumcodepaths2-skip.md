---
title: IEnumCodePaths2::Skip | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCodePaths2::Skip
helpviewer_keywords:
- IEnumCodePaths2::Skip
ms.assetid: 356472d8-68b2-4b7e-b5f0-1f16d4ee80af
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b635053765dafa0fdb83dc0ab29e646b816d0aa5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319659"
---
# <a name="ienumcodepaths2skip"></a>IEnumCodePaths2::Skip
Omite el número especificado de elementos.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Skip(
   ULONG celt
);
```

```csharp
int Skip(
   uint celt
);
```

## <a name="parameters"></a>Parámetros
`celt`\
[in] Número de elementos que se van a omitir.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si `celt` es mayor que el número de elementos restantes; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Si `celt` especifica un valor mayor que el número de elementos restantes, la enumeración se establece en el extremo y `S_FALSE` se devuelve.

## <a name="see-also"></a>Vea también
- [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)