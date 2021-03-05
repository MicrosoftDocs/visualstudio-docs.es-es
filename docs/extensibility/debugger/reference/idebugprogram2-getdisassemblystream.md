---
description: Obtiene la secuencia de desensamblado para este programa o parte de este programa.
title: 'IDebugProgram2:: GetDisassemblyStream | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDisassemblyStream
helpviewer_keywords:
- IDebugProgram2::GetDisassemblyStream
ms.assetid: beda0da5-267e-4bf3-96c4-b659d29e2254
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e000ada618c21af865743bfb2bd9fd6b60a80a4b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159931"
---
# <a name="idebugprogram2getdisassemblystream"></a>IDebugProgram2::GetDisassemblyStream
Obtiene la secuencia de desensamblado para este programa o parte de este programa.

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
de Especifica un valor de la enumeración [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) que define el ámbito de la secuencia de desensamblado.

`pCodeContext`\
de Objeto [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) que representa la posición en la que se va a iniciar la secuencia de desensamblado.

`ppDisassemblyStream`\
enuncia Devuelve un objeto [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) que representa la secuencia del desensamblado.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error. Devuelve `E_DISASM_NOTSUPPORTED` si no se admite el desensamblado para esta arquitectura en particular.

## <a name="remarks"></a>Observaciones
 Si el `dwScopes` parámetro tiene la `DSS_HUGE` marca de la enumeración [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) establecida, se espera que el desensamblado devuelva un gran número de instrucciones de desensamblado, por ejemplo, para un archivo o módulo completo. Si `DSS_HUGE` no se establece la marca, se espera que el desensamblado se limite a una región pequeña, normalmente la de una sola función.

## <a name="see-also"></a>Consulte también
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
