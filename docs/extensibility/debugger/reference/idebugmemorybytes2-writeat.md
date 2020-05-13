---
title: IDebugMemoryBytes2::WriteAt ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::WriteAt
helpviewer_keywords:
- IDebugMemoryBytes2::WriteAt method
- WriteAt method
ms.assetid: 61cc3704-47fa-4d9b-aa62-bb4585ac8fb1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ac9113424c6cd5cce230774a6e5335ffa4d4ba77
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727516"
---
# <a name="idebugmemorybytes2writeat"></a>IDebugMemoryBytes2::WriteAt
Escribe el número especificado de bytes de memoria, comenzando en la dirección especificada.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT WriteAt( 
   IDebugMemoryContext2* pStartContext,
   DWORD                 dwCount,
   BYTE*                 rgbMemory
);
```

```csharp
int WriteAt(
   IDebugMemoryContext2 pStartContext,
   uint                 dwCount,
   byte[]               rgbMemory
);
```

## <a name="parameters"></a>Parámetros
`pStartContext`\
[en] El [objeto IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) que especifica dónde empezar a escribir bytes.

`dwCount`\
[in] Número de bytes que se van a escribir.

`rgbMemory`\
[en] Los bytes que se van a escribir. Se supone que esta `dwCount` matriz tiene al menos bytes de tamaño.

## <a name="return-value"></a>Valor devuelto
 Si se `S_OK`realiza correctamente, devuelve ; de lo `S_FALSE` contrario, devuelve si no se podrían `E_FAIL`escribir todos los bytes o devuelve un código de error (normalmente).

## <a name="remarks"></a>Observaciones
 Si la dirección inicial no está dentro de la ventana de memoria representada por este `E_FAIL` [objeto IDebugMemoryBytes2,](../../../extensibility/debugger/reference/idebugmemorybytes2.md) no se produce ninguna escritura y se devuelve un código de error de, incluso si la cantidad de escritura se superpone en el espacio de memoria.

## <a name="see-also"></a>Vea también
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
