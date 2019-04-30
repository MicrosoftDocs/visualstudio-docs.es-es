---
title: IDebugProgram2::GetDisassemblyStream | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDisassemblyStream
helpviewer_keywords:
- IDebugProgram2::GetDisassemblyStream
ms.assetid: beda0da5-267e-4bf3-96c4-b659d29e2254
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bcc5032fe2fa080034cda3f63a0fb013e12c42e3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62870399"
---
# <a name="idebugprogram2getdisassemblystream"></a>IDebugProgram2::GetDisassemblyStream
Obtiene la secuencia de desensamblado de este programa o una parte de este programa.

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

#### <a name="parameters"></a>Parámetros
 `dwScope`

 [in] Especifica un valor de la [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) enumeración que define el ámbito de la secuencia de desensamblado.

 `pCodeContext`

 [in] Un [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) objeto que representa la posición de dónde comenzar la secuencia de desensamblado.

 `ppDisassemblyStream`

 [out] Devuelve un [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) objeto que representa la secuencia de desensamblado.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error. Devuelve `E_DISASM_NOTSUPPORTED` si el Desensamblador no es compatible con esta arquitectura determinada.

## <a name="remarks"></a>Comentarios
 Si el `dwScopes` parámetro tiene el `DSS_HUGE` marca de la [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) enumeración establecido, el desensamblado se espera que devuelva un gran número de instrucciones de desensamblado, por ejemplo, para un archivo completo o módulo. Si el `DSS_HUGE` marca no se establece, a continuación, se espera que el desensamblado se limita a un área pequeño, normalmente que el de una sola función.

## <a name="see-also"></a>Vea también
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)