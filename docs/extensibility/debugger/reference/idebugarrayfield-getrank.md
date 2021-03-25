---
description: Obtiene el rango o el número de dimensiones de la matriz.
title: 'IDebugArrayField:: Getrank (| Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetRank
helpviewer_keywords:
- IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1ac945e23090b649ffb5ad2f452ec9245aac81ad
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058981"
---
# <a name="idebugarrayfieldgetrank"></a>IDebugArrayField::GetRank
Obtiene el rango o el número de dimensiones de la matriz.

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
 El rango de una matriz se corresponde con el número de dimensiones. En C++ y C#, las matrices multidimensionales son realmente matrices de matrices y, por tanto, se pueden considerar solo una matriz unidimensional (y el `GetRank` método siempre devuelve 1). Por [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] otro lado, las matrices multidimensionales se tratan de forma diferente y el rango de una matriz de este tipo refleja el número de dimensiones (y el `GetRank` método siempre devuelve el número de dimensiones).

## <a name="see-also"></a>Consulte también
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
