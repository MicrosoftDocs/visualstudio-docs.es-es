---
title: IDebugMemoryContext2::Subtract ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Subtract
helpviewer_keywords:
- Subtract method
- IDebugMemoryContext2::Subtract method
ms.assetid: 63df14c7-8d7e-47c1-afa7-5a1ab5d8eaba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c858beb8c3f9f587633dbae8b3b1fe73fd789663
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727437"
---
# <a name="idebugmemorycontext2subtract"></a>IDebugMemoryContext2::Subtract
Resta el valor especificado del contexto actual y devuelve un nuevo contexto.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Subtract( 
   UINT64                 dwCount,
   IDebugMemoryContext2** ppMemCxt
);
```

```csharp
int Subtract(
   ulong                    dwCount,
   out IDebugMemoryContext2 ppMemCxt
);
```

## <a name="parameters"></a>Parámetros
`dwCount`\
[en] El número de bytes de memoria a disminuir.

`ppMemCxt`\
[fuera] Devuelve un nuevo [iDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) objeto.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Un contexto de memoria es una dirección, por lo que restar un valor de una dirección genera una nueva dirección que requiere una nueva interfaz de contexto.

 Este método siempre debe producir un nuevo contexto, incluso si la dirección resultante está fuera del espacio de memoria asociado a este contexto. La única excepción a esto es si no se `ppMemCxt` puede asignar memoria para el nuevo contexto o si es un valor nulo (que es un error).

## <a name="see-also"></a>Vea también
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
