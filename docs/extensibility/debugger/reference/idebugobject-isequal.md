---
description: Compara un objeto con este objeto.
title: 'IDebugObject:: IsEqual | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsEqual
helpviewer_keywords:
- IDebugObject::IsEqual method
ms.assetid: 4b76e663-ef2e-41ff-9be1-bf26d666a34a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0907b72f2a0647fc6ff6181ecdc5c7fd8c2134cb
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151667"
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
de Objeto [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa el objeto con el que se va a comparar.

`pfIsEqual`\
enuncia Devuelve un valor distinto de cero ( `TRUE` ) si los valores de los objetos son iguales; de lo contrario, devuelve cero ( `FALSE` ).

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Normalmente, este método puede comparar las direcciones de los valores representados por el `pObject` parámetro y este objeto [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) ; si las direcciones son iguales, los objetos se pueden considerar iguales.

## <a name="see-also"></a>Consulte también
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
