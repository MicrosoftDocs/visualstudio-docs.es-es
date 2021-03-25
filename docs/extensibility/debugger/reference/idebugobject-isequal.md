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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cff388778ea584f589f92b5dc9dab11c060c953c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054093"
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
