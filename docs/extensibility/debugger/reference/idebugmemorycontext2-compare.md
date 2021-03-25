---
description: Compara el contexto de memoria con cada contexto de la matriz dada de la manera indicada por las marcas de comparación y devuelve un índice del primer contexto que coincide con.
title: 'IDebugMemoryContext2:: Compare | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Compare
helpviewer_keywords:
- IDebugMemoryContext2::Compare method
- Compare method
ms.assetid: c51b5128-848e-4d8e-b2e9-1161339763c3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 67acecafd677d5096e1bf975f85e21a5c6cbe133
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076776"
---
# <a name="idebugmemorycontext2compare"></a>IDebugMemoryContext2::Compare
Compara el contexto de memoria con cada contexto de la matriz dada de la manera indicada por las marcas de comparación y devuelve un índice del primer contexto que coincide con.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Compare( 
   CONTEXT_COMPARE        compare,
   IDebugMemoryContext2** rgpMemoryContextSet,
   DWORD                  dwMemoryContextSetLen,
   DWORD*                 pdwMemoryContext
);
```

```csharp
int Compare(
   enum_CONTEXT_COMPARE   compare,
   IDebugMemoryContext2[] rgpMemoryContextSet,
   uint                   dwMemoryContextSetLen,
   out uint               pdwMemoryContext
);
```

## <a name="parameters"></a>Parámetros
`compare`\
de Un valor de la enumeración [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md) que determina el tipo de comparación.

`rgpMemoryContextSet`\
de Una matriz de referencias a los objetos [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) con los que se va a comparar.

`dwMemoryContextSetLen`\
de Número de contextos de la `rgpMemoryContextSet` matriz.

`pdwMemoryContext`\
enuncia Devuelve el índice del primer contexto de memoria que satisface la comparación.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error. Devuelve `E_COMPARE_CANNOT_COMPARE` si no se pueden comparar los dos contextos.

## <a name="remarks"></a>Observaciones
 Un motor de depuración (de) no tiene que admitir todos los tipos de comparaciones, pero debe admitir al menos `CONTEXT_EQUAL` , `CONTEXT_LESS_THAN` `CONTEXT_GREATER_THAN` y `CONTEXT_SAME_SCOPE` .

## <a name="see-also"></a>Consulte también
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
- [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md)
