---
title: IDebugProgram2::GetDisassemblyStream | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgram2::GetDisassemblyStream
helpviewer_keywords:
- IDebugProgram2::GetDisassemblyStream
ms.assetid: beda0da5-267e-4bf3-96c4-b659d29e2254
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 343b818352a9cdec5518788ec9a2969c36153331
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51741997"
---
# <a name="idebugprogram2getdisassemblystream"></a>IDebugProgram2::GetDisassemblyStream
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtiene la secuencia de desensamblado de este programa o una parte de este programa.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)

