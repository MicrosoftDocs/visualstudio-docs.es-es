---
title: IDebugArrayField::GetRank ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetRank
helpviewer_keywords:
- IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 692f2f13d861d9688ba349fbc80cb1ca426582c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736312"
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
[fuera] Devuelve el rango.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve S_OK; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 El rango de una matriz corresponde al número de dimensiones. En C++ y C, las matrices multidimensionales son realmente matrices de matrices y, `GetRank` por lo tanto, se pueden considerar solo una matriz unidimensional (y el método siempre devuelve 1). En [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)], por otro lado, las matrices multidimensionales se manejan de manera diferente y el `GetRank` rango de dicha matriz refleja el número de dimensiones (y el método siempre devuelve el número de dimensiones).

## <a name="see-also"></a>Vea también
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
