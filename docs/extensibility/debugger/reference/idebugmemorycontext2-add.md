---
title: IDebugMemoryContext2::Add ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Add
helpviewer_keywords:
- IDebugMemoryContext2::Add method
- Add method
ms.assetid: 3c47e646-ce9e-4dd3-8f1a-6dbd3827d407
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a21fa2ec6d48bb1d6bf17bbc0d2ebf0d90a25a9f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727481"
---
# <a name="idebugmemorycontext2add"></a>IDebugMemoryContext2::Add
Agrega el valor especificado al contexto actual y devuelve un nuevo contexto.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Add( 
   UINT64                 dwCount,
   IDebugMemoryContext2** ppMemCxt
);
```

```csharp
int Add(
   ulong                    dwCount,
   out IDebugMemoryContext2 ppMemCxt
);
```

## <a name="parameters"></a>Parámetros
`dwCount`\
[en] El valor que se va a agregar al contexto actual.

`ppMemCxt`\
[fuera] Devuelve un nuevo [iDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) objeto.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Un contexto de memoria es una dirección, por lo que agregar un valor a una dirección genera una nueva dirección que requiere una nueva interfaz de contexto.

 Este método siempre debe producir un nuevo contexto, incluso si la dirección resultante está fuera del espacio de memoria asociado a este contexto. La única excepción a esto es si no se `ppMemCxt` puede asignar memoria para el nuevo contexto o si es un valor nulo (que es un error).

## <a name="see-also"></a>Vea también
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
