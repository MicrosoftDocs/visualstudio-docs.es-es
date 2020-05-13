---
title: IDebugArrayObject::GetDimensions ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetDimensions
helpviewer_keywords:
- IDebugArrayObject::GetDimensions method
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 527f79724aeac0de58d0ae63c9c2408ed2eca9ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736159"
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
[en] El número de dimensiones que se van a recuperar.

`dwDimensions`\
[adentro, fuera] Matriz que se rellena con los tamaños de cada dimensión. `dwCount`especifica el tamaño máximo `dwDimensions` de la matriz.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve S_OK; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Una matriz multidimensional puede tener tamaños diferentes para cada dimensión. Por ejemplo, dada la `myarray[3][2][6]`matriz tridimensional , este método devolvería `dwDimensions` 3, 2 y 6 en el parámetro en ese orden.

## <a name="see-also"></a>Vea también
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
