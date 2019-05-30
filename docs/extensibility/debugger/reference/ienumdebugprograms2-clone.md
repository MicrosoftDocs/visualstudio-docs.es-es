---
title: IEnumDebugPrograms2::Clone | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2::Clone
helpviewer_keywords:
- IEnumDebugPrograms2::Clone
ms.assetid: 880846c2-39d3-45cd-85c3-ad5409a3710f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7fd4f8719fdd5f587d1ac5305245f87ff1fd65d2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317128"
---
# <a name="ienumdebugprograms2clone"></a>IEnumDebugPrograms2::Clone
Devuelve una copia de la enumeración actual como un objeto independiente.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Clone(
   IEnumDebugPrograms2** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugPrograms2 ppEnum
);
```

## <a name="parameters"></a>Parámetros
`ppEnum`\
[out] Devuelve una copia de esta enumeración como un objeto independiente.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 La copia de la enumeración tiene el mismo estado que el original en el momento en que se llama a este método. Sin embargo, los Estados de la copia y el original son independientes y se pueden cambiar de forma individual.

## <a name="see-also"></a>Vea también
- [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)