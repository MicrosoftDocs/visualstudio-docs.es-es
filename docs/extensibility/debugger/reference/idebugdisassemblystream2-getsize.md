---
description: Obtiene el tamaño en las instrucciones de esta secuencia de desensamblado.
title: 'IDebugDisassemblyStream2:: se obtiene | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetSize
helpviewer_keywords:
- IDebugDisassemblyStream2::GetSize
ms.assetid: 8f512704-12d0-46d2-959a-4f8dffe117b5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 94207c8e14306049068e838971aa778290de2ba6
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154371"
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
enuncia Devuelve el tamaño, en instrucciones.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 El valor devuelto por este método se puede usar para asignar una matriz de estructuras [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) que se pasa a continuación al método [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) .

## <a name="see-also"></a>Consulte también
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [Lectura](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
