---
title: 'IDebugMemoryContext2:: Add | Microsoft Docs'
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
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4ddba5665ead15bb623193412bafa7d6eaa8aa16
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851223"
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
de Valor que se va a agregar al contexto actual.

`ppMemCxt`\
enuncia Devuelve un nuevo objeto [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) .

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Notas
 Un contexto de memoria es una dirección, por lo que agregar un valor a una dirección genera una nueva dirección que requiere una nueva interfaz de contexto.

 Este método siempre debe generar un nuevo contexto, incluso si la dirección resultante está fuera del espacio de memoria asociado a este contexto. La única excepción es si no se puede asignar memoria para el nuevo contexto o si `ppMemCxt` es un valor null (que es un error).

## <a name="see-also"></a>Vea también
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
