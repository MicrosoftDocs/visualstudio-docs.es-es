---
description: Obtiene el número de elementos de la matriz.
title: 'IDebugArrayField:: GetNumberOfElements | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetNumberOfElements
helpviewer_keywords:
- IDebugArrayField::GetNumberOfElements method
ms.assetid: a1961ef3-d69d-4022-b8c9-b9cfb9811345
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4b5c3daee373c5803926dc259564dab18dfe5852
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058955"
---
# <a name="idebugarrayfieldgetnumberofelements"></a>IDebugArrayField::GetNumberOfElements
Obtiene el número de elementos de la matriz.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetNumberOfElements( 
   DWORD* pdwNumElements
);
```

```csharp
int GetNumberOfElements(
   out uint pdwNumElements
);
```

## <a name="parameters"></a>Parámetros
`pdwNumElements`\
enuncia Devuelve el número de elementos de la matriz.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 El valor devuelto es el número total de elementos de la matriz, independientemente del número de dimensiones.

## <a name="see-also"></a>Consulte también
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
