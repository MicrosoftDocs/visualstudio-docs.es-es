---
description: Resta el valor especificado del contexto actual y devuelve un nuevo contexto.
title: 'IDebugMemoryContext2:: restar | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Subtract
helpviewer_keywords:
- Subtract method
- IDebugMemoryContext2::Subtract method
ms.assetid: 63df14c7-8d7e-47c1-afa7-5a1ab5d8eaba
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1007a50ca42164cfc4e4f58c8d2c877cbba20f5c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058591"
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

## <a name="see-also"></a>Consulte también
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
