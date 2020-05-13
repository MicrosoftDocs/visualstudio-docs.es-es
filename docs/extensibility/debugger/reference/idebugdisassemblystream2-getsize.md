---
title: IDebugDisassemblyStream2::GetSize ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetSize
helpviewer_keywords:
- IDebugDisassemblyStream2::GetSize
ms.assetid: 8f512704-12d0-46d2-959a-4f8dffe117b5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 75fa12b1e9e70601626667dd3707f1e230f5de0c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732103"
---
# <a name="idebugdisassemblystream2getsize"></a>IDebugDisassemblyStream2::GetSize
Obtiene el tamaño en las instrucciones de esta secuencia de desensamblado.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetSize( 
   UINT64* pnSize
);
```

```csharp
int GetSize( 
   out ulong pnSize
);
```

## <a name="parameters"></a>Parámetros
`pnSize`\
[fuera] Devuelve el tamaño, en las instrucciones.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 El valor devuelto por este método se puede utilizar para asignar una matriz de [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) estructuras que, a continuación, se pasa a la [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) método.

## <a name="see-also"></a>Vea también
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [Lectura](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
