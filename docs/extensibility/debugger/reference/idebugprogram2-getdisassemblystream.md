---
title: IDebugProgram2::GetDisassemblyStream | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::GetDisassemblyStream
helpviewer_keywords:
- IDebugProgram2::GetDisassemblyStream
ms.assetid: beda0da5-267e-4bf3-96c4-b659d29e2254
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f5b991a877f91b9324b6535fb3b79b082cd901c2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
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
 [in] Un [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) objeto que representa la posición de la que desea iniciar la secuencia de desensamblado.  
  
 `ppDisassemblyStream`  
 [out] Devuelve un [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) objeto que representa el flujo de desensamblado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error. Devuelve `E_DISASM_NOTSUPPORTED` si desensamblado no es compatible con esta arquitectura determinada.  
  
## <a name="remarks"></a>Comentarios  
 Si el `dwScopes` parámetro tiene el `DSS_HUGE` marca de la [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) conjunto de enumeración, a continuación, se espera el desensamblador para devolver un gran número de instrucciones de desensamblado, por ejemplo, para un archivo completo o el módulo. Si el `DSS_HUGE` no se estableció el marcador, a continuación, se espera que el desensamblado se limita a un área pequeño, normalmente que el de una sola función.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)