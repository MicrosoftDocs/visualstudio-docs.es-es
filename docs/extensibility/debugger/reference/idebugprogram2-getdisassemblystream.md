---
title: IDebugProgram2::GetDisassemblyStream ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDisassemblyStream
helpviewer_keywords:
- IDebugProgram2::GetDisassemblyStream
ms.assetid: beda0da5-267e-4bf3-96c4-b659d29e2254
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2160f963ad1f3f37291519ced30b8096e33a6116
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722865"
---
# <a name="idebugprogram2getdisassemblystream"></a>IDebugProgram2::GetDisassemblyStream
Obtiene la secuencia de desensamblado para este programa o una parte de este programa.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetDisassemblyStream( 
   DISASSEMBLY_STREAM_SCOPE   dwScope,
   IDebugCodeContext2*        pCodeContext,
   IDebugDisassemblyStream2** ppDisassemblyStream
);
```

```csharp
int GetDisassemblyStream( 
   enum_DISASSEMBLY_STREAM_SCOPE  dwScope,
   IDebugCodeContext2             pCodeContext,
   out IDebugDisassemblyStream2   ppDisassemblyStream
);
```

## <a name="parameters"></a>Parámetros
`dwScope`\
[en] Especifica un valor de la [enumeración DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) que define el ámbito de la secuencia de desensamblado.

`pCodeContext`\
[en] Un [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) objeto que representa la posición de dónde iniciar la secuencia de desensamblado.

`ppDisassemblyStream`\
[fuera] Devuelve un [objeto IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) que representa la secuencia de desensamblado.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error. Devuelve `E_DISASM_NOTSUPPORTED` si no se admite el desensamblado para esta arquitectura concreta.

## <a name="remarks"></a>Observaciones
 Si `dwScopes` el parámetro `DSS_HUGE` tiene la marca del [conjunto de enumeración DISASSEMBLY_STREAM_SCOPE,](../../../extensibility/debugger/reference/disassembly-stream-scope.md) se espera que el desensamblado devuelva un gran número de instrucciones de desensamblado, por ejemplo, para un archivo o módulo completo. Si `DSS_HUGE` no se establece la marca, se espera que el desensamblado se limite a una región pequeña, normalmente la de una sola función.

## <a name="see-also"></a>Vea también
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
