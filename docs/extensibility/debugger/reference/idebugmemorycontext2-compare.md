---
title: IDebugMemoryContext2::Compare ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Compare
helpviewer_keywords:
- IDebugMemoryContext2::Compare method
- Compare method
ms.assetid: c51b5128-848e-4d8e-b2e9-1161339763c3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4b2551f8554d96186b90a1eed97a5a48ec5f0405
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727496"
---
# <a name="idebugmemorycontext2compare"></a>IDebugMemoryContext2::Compare
Compara el contexto de memoria con cada contexto de la matriz dada de la manera indicada por los indicadores compare, devolviendo un índice del primer contexto que coincida.

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
[en] Valor de la [enumeración CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md) que determina el tipo de comparación.

`rgpMemoryContextSet`\
[en] Matriz de referencias a los objetos [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) con los que se va a comparar.

`dwMemoryContextSetLen`\
[en] El número de contextos de la `rgpMemoryContextSet` matriz.

`pdwMemoryContext`\
[fuera] Devuelve el índice del primer contexto de memoria que satisface la comparación.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error. Devuelve `E_COMPARE_CANNOT_COMPARE` si no se pueden comparar los dos contextos.

## <a name="remarks"></a>Observaciones
 Un motor de depuración (DE) no tiene que admitir todos `CONTEXT_EQUAL`los `CONTEXT_LESS_THAN` `CONTEXT_GREATER_THAN` tipos `CONTEXT_SAME_SCOPE`de comparaciones, pero debe admitir al menos , , y .

## <a name="see-also"></a>Vea también
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
- [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md)
