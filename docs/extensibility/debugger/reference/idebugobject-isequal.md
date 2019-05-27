---
title: IDebugObject::IsEqual | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsEqual
helpviewer_keywords:
- IDebugObject::IsEqual method
ms.assetid: 4b76e663-ef2e-41ff-9be1-bf26d666a34a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 527d0bf7dcc7841516c3ae620130aa346841d0a1
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/24/2019
ms.locfileid: "66202869"
---
# <a name="idebugobjectisequal"></a>IDebugObject::IsEqual
Compara un objeto con este objeto.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT IsEqual( 
   IDebugObject* pObject,
   BOOL*         pfIsEqual
);
```

```csharp
int IsEqual(
   IDebugObject pObject,
   out int      pfIsEqual
);
```

## <a name="parameters"></a>Parámetros
`pObject`\
[in] Un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa el objeto que se compara con el objeto.

`pfIsEqual`\
[out] Devuelve cero (`TRUE`) si los valores de los objetos son iguales; en caso contrario, devuelve cero (`FALSE`).

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Normalmente, este método puede comparar las direcciones de los valores representados por el `pObject` parámetro y esto [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objeto; si las direcciones son iguales, los objetos se consideran iguales.

## <a name="see-also"></a>Vea también
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)