---
description: Crea un objeto de matriz.
title: 'IDebugFunctionObject:: CreateArrayObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateArrayObject
helpviewer_keywords:
- IDebugFunctionObject::CreateArrayObject method
ms.assetid: a380e53c-15f1-401f-927f-f366eea789e6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 94216521f0a57a76f83c68f168ed1afcac199a0e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073552"
---
# <a name="idebugfunctionobjectcreatearrayobject"></a>IDebugFunctionObject::CreateArrayObject
Crea un objeto de matriz. Esta matriz puede contener valores primitivos o de instancia de objeto.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT CreateArrayObject( 
   OBJECT_TYPE    ot,
   IDebugField*   pClassField,
   DWORD          dwRank,
   DWORD          dwDims[],
   DWORD          dwLowBounds[],
   IDebugObject** ppObject
);
```

```csharp
int CreateArrayObject(
   enum_OBJECT_TYPE ot,
   IDebugField      pClassField,
   uint             dwRank,
   uint[]           dwDims,
   uint[]           dwLowBounds,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parámetros
`ot`\
de Especifica un valor de la enumeración [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) que indica el tipo del nuevo objeto de matriz.

`pClassField`\
de Un objeto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que representa la clase de un objeto, si se crea una matriz de valores de instancia de objeto. Si crea una matriz de objetos primitivos, este parámetro es un valor nulo.

`dwRank`\
de El rango o el número de dimensiones de la matriz.

`dwDims`\
de Los tamaños de cada dimensión de la matriz.

`dwLowBounds`\
de El origen de cada dimensión (normalmente 0 o 1).

`ppObject`\
enuncia Devuelve un objeto [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa la matriz recién creada. En realidad, se trata de un objeto [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) .

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Llame a este método para crear un objeto que represente un parámetro de matriz a la función representada por la interfaz [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .

## <a name="see-also"></a>Consulte también
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
