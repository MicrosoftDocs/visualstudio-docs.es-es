---
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
ms.openlocfilehash: 5fe662f6e6ed2db50fb905ad8918a7b7216853f3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870108"
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

## <a name="remarks"></a>Notas
 Use el método [getdimensions (](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md) para recuperar el tamaño de cada dimensión del objeto de matriz.

## <a name="see-also"></a>Vea también
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
