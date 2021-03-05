---
description: Obtiene el ámbito de la secuencia de desensamblado.
title: 'IDebugDisassemblyStream2:: Getscope (| Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetScope
helpviewer_keywords:
- IDebugDisassemblyStream2::GetScope
ms.assetid: 71c6e632-642a-42d8-a995-77e4ac190a5b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8b112975649ec477a036826e3dc938ba756615c0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154462"
---
# <a name="idebugdisassemblystream2getscope"></a>IDebugDisassemblyStream2::GetScope
Obtiene el ámbito de la secuencia de desensamblado.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetScope( 
   DISASSEMBLY_STREAM_SCOPE* pdwScope
);
```

```csharp
int GetScope( 
   out enum_ DISASSEMBLY_STREAM_SCOPE pdwScope
);
```

## <a name="parameters"></a>Parámetros
`pdwScope`\
enuncia Devuelve un valor de la enumeración [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) que describe el ámbito de esta secuencia de desensamblado.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 El ámbito de un desensamblado podría ser una función o todo el módulo, por ejemplo.

## <a name="see-also"></a>Consulte también
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)
