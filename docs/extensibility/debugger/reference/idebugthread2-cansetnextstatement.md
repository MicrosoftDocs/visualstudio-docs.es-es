---
title: IDebugThread2::CanSetNextStatement | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugThread2::CanSetNextStatement
helpviewer_keywords:
- IDebugThread2::CanSetNextStatement
ms.assetid: 7014af80-ff4f-4790-a34b-0528918d1fa3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dcb5ef43f30ca40454cde19a2afde229de6a9ea3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53924441"
---
# <a name="idebugthread2cansetnextstatement"></a>IDebugThread2::CanSetNextStatement
Determina si se puede establecer el puntero de instrucción actual en el marco de pila determinado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT CanSetNextStatement (   
   IDebugStackFrame2*  pStackFrame,  
   IDebugCodeContext2* pCodeContext  
);  
```  
  
```csharp  
int CanSetNextStatement (   
   IDebugStackFrame2  pStackFrame,  
   IDebugCodeContext2 pCodeContext  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pStackFrame`  
 Reservado para uso futuro; se establece en un valor null. Si se trata de un valor null, utilice el marco de pila actual.  
  
 `pCodeContext`  
 [in] Un [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) objeto que describe la ubicación del código va a ejecutar y su contexto.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Si este método devuelve `S_OK`, a continuación, llame a la [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md) método para establecer la siguiente instrucción.  
  
## <a name="see-also"></a>Vea también  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)