---
description: Obtiene el rango de la matriz, es decir, el número de dimensiones.
title: 'IDebugArrayObject:: Getrank (| Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetRank
helpviewer_keywords:
- IDebugArrayObject::GetRank method
ms.assetid: 9948551a-e334-4ff6-979c-08dab633b9b6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3a246cda3f5b9395ae013b4bca9d4d27d6f8a5c1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158545"
---
# <a name="idebugarrayobjectgetrank"></a>IDebugArrayObject::GetRank
Obtiene el rango de la matriz, es decir, el número de dimensiones.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetRank( 
   DWORD* pdwRank
);
```

```csharp
int GetRank(
   out uint pdwRank
);
```

## <a name="parameters"></a>Parámetros
`pdwRank`\
enuncia Devuelve el rango.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Use el método [getdimensions (](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md) para recuperar el tamaño de cada dimensión del objeto de matriz.

## <a name="see-also"></a>Consulte también
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
