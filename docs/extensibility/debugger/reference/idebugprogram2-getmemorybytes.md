---
description: Recupera los bytes de memoria ocupados por el programa.
title: 'IDebugProgram2:: GetMemoryBytes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetMemoryBytes
helpviewer_keywords:
- IDebugProgram2::GetMemoryBytes
ms.assetid: 1cdedb47-caf8-468e-aaf4-163f16afb403
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 27b3ce2dda13e45bb4d82f68eb02a8930de55764
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053690"
---
# <a name="idebugprogram2getmemorybytes"></a>IDebugProgram2::GetMemoryBytes
Recupera los bytes de memoria ocupados por el programa.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetMemoryBytes( 
   IDebugMemoryBytes2** ppMemoryBytes
);
```

```csharp
int GetMemoryBytes( 
   out IDebugMemoryBytes2 ppMemoryBytes
);
```

## <a name="parameters"></a>Parámetros
`ppMemoryBytes`\
enuncia Devuelve un objeto [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) que representa los bytes de memoria del programa.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Los bytes de memoria que representa el objeto [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) son para la imagen del programa en la memoria y no para la memoria asignada cuando se ejecutó el programa.

## <a name="see-also"></a>Consulte también
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
