---
description: Escribe el número especificado de bytes de memoria, comenzando en la dirección especificada.
title: 'IDebugMemoryBytes2:: WriteAt | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::WriteAt
helpviewer_keywords:
- IDebugMemoryBytes2::WriteAt method
- WriteAt method
ms.assetid: 61cc3704-47fa-4d9b-aa62-bb4585ac8fb1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 64e8aed5586dc6e2abf33b540654dcd24437e746
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076815"
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
de El objeto [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) que especifica dónde empezar a escribir los bytes.

`dwCount`\
[in] Número de bytes que se van a escribir.

`rgbMemory`\
de Bytes que se van a escribir. Se supone que la matriz tiene un `dwCount` tamaño de bytes como mínimo.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve `S_FALSE` si no se pueden escribir todos los bytes o devuelve un código de error (normalmente `E_FAIL` ).

## <a name="remarks"></a>Observaciones
 Si la dirección inicial no está dentro de la ventana memoria representada por este objeto [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) , no se produce ninguna escritura y se devuelve un código de error `E_FAIL` , incluso si la cantidad que se va a escribir se superpone en el espacio de memoria.

## <a name="see-also"></a>Consulte también
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
