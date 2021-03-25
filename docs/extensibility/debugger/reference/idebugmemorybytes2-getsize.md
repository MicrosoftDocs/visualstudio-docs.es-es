---
description: Recupera el tamaño, en bytes, de la memoria representada por este objeto IDebugMemoryBytes2.
title: 'IDebugMemoryBytes2:: se obtiene | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::GetSize
helpviewer_keywords:
- IDebugMemoryBytes2::GetSize method
- GetSize method
ms.assetid: dae64c5f-5b54-40c3-b32f-ec3b16c093f7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8c76b9061bd5b54e222f7092720e29805aba028b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076789"
---
# <a name="idebugmemorybytes2getsize"></a>IDebugMemoryBytes2::GetSize
Recupera el tamaño, en bytes, de la memoria representada por este objeto [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) .

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetSize( 
   UINT64* pqwSize
);
```

```csharp
int GetSize(
   out ulong pqwSize
);
```

## <a name="parameters"></a>Parámetros
`pqwSize`\
enuncia Devuelve el tamaño, en bytes, del espacio de memoria.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Consulte también
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
