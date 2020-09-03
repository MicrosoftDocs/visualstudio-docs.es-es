---
title: 'IDebugMemoryContext2:: restar | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
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
de Número de bytes de memoria que se van a reducir.

`ppMemCxt`\
enuncia Devuelve un nuevo objeto [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) .

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Un contexto de memoria es una dirección, por lo que restar un valor de una dirección genera una nueva dirección que requiere una nueva interfaz de contexto.

 Este método siempre debe generar un nuevo contexto, incluso si la dirección resultante está fuera del espacio de memoria asociado a este contexto. La única excepción es si no se puede asignar memoria para el nuevo contexto o si `ppMemCxt` es un valor null (que es un error).

## <a name="see-also"></a>Vea también
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
