---
title: IDebugObject::IsNullReference | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsNullReference
helpviewer_keywords:
- IDebugObject::IsNullReference method
ms.assetid: 6dbfcdb0-954f-4486-8fac-7ea8d003e3a9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1fb6b5c0692ec43feec0cf4de48d9ce730b0032e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323517"
---
# <a name="idebugobjectisnullreference"></a>IDebugObject::IsNullReference
Comprueba si este objeto es una referencia nula.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT IsNullReference( 
   BOOL* pfIsNull
);
```

```csharp
int IsNullReference(
   out int pfIsNull
);
```

## <a name="parameters"></a>Parámetros
`pfIsNull`\
[out] Devuelve cero (`TRUE`) si este objeto es una referencia null; en caso contrario, devuelve cero (`FALSE`).

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Una referencia null significa que un objeto vacío o un objeto que no se ha asignado a.

## <a name="see-also"></a>Vea también
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)