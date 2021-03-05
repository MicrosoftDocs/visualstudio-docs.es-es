---
description: Obtiene las dimensiones de la matriz.
title: 'IDebugArrayObject:: Getdimensions (| Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetDimensions
helpviewer_keywords:
- IDebugArrayObject::GetDimensions method
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f5bb935ea4aba6ab6ebd0a39f8dfc8d539d6555c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158688"
---
# <a name="idebugarrayobjectgetdimensions"></a>IDebugArrayObject::GetDimensions
Obtiene las dimensiones de la matriz.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetDimensions( 
   DWORD dwCount,
   DWORD dwDimensions[]
);
```

```csharp
int GetDimensions(
   [In] uint    dwCount,
   [Out] uint[] dwDimensions
);
```

## <a name="parameters"></a>Parámetros
`dwCount`\
de Número de dimensiones que se van a recuperar.

`dwDimensions`\
[in, out] Matriz que se rellena con los tamaños de cada dimensión. `dwCount` especifica el tamaño máximo de la `dwDimensions` matriz.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Una matriz multidimensional puede tener distintos tamaños para cada dimensión. Por ejemplo, dada la matriz tridimensional `myarray[3][2][6]` , este método devolvería 3, 2 y 6 en el `dwDimensions` parámetro en ese orden.

## <a name="see-also"></a>Consulte también
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
