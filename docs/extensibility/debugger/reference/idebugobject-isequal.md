---
title: IDebugObject::IsEqual ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsEqual
helpviewer_keywords:
- IDebugObject::IsEqual method
ms.assetid: 4b76e663-ef2e-41ff-9be1-bf26d666a34a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 13018e31fb5f8bed89a0a290d687360a605a855d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726503"
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
[en] Un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objeto que representa el objeto que se va a comparar.

`pfIsEqual`\
[fuera] Devuelve distinto de`TRUE`cero ( ) si los valores de los objetos son iguales; de lo contrario, devuelve cero (`FALSE`).

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve S_OK; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Normalmente, este método puede comparar las direcciones `pObject` de los valores representados por el parámetro y este [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objeto; si las direcciones son iguales, entonces los objetos se pueden considerar iguales.

## <a name="see-also"></a>Vea también
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
