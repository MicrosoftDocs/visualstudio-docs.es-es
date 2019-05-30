---
title: IEnumCodePaths2::Reset | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCodePaths2::Reset
helpviewer_keywords:
- IEnumCodePaths2::Reset
ms.assetid: 490c0e19-ff4b-4673-bd06-cdee996ac226
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 18504e8cfb40614c4725456ab5c73c74231a3b7b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319618"
---
# <a name="ienumcodepaths2reset"></a>IEnumCodePaths2::Reset
Restablece la enumeración al primer elemento.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Reset(
   void
);
```

```csharp
int Reset();
```

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Después de llamar a este método, la siguiente llamada a la [siguiente](../../../extensibility/debugger/reference/ienumcodepaths2-next.md) método devuelve el primer elemento de la enumeración.

## <a name="see-also"></a>Vea también
- [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)