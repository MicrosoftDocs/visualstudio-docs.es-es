---
title: IDebugThread2::SetNextStatement | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugThread2::SetNextStatement
helpviewer_keywords:
- IDebugThread2::SetNextStatement
ms.assetid: 9e2834dd-4ecf-45af-8e6c-f9318ebdac06
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f8d5074dab25b539a7243b800abf8b6fa505bd8f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54949342"
---
# <a name="idebugthread2setnextstatement"></a>IDebugThread2::SetNextStatement
Establece el puntero de instrucción actual en el contexto de código dado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT SetNextStatement (   
   IDebugStackFrame2*  pStackFrame,  
   IDebugCodeContext2* pCodeContext  
);  
```  
  
```csharp  
int SetNextStatement (   
   IDebugStackFrame2  pStackFrame,  
   IDebugCodeContext2 pCodeContext  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pStackFrame`  
 Reservado para uso futuro; se establece en un valor null.  
  
 `pCodeContext`  
 [in] Un [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) objeto que describe la ubicación del código va a ejecutar y su contexto.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error. En la tabla siguiente se muestra otros posibles valores.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|E_CANNOT_SET_NEXT_STATEMENT_ON_NONLEAF_FRAME|La siguiente instrucción no puede ser un marco de pila más profundo en la pila del marco.|  
|E_CANNOT_SETIP_TO_DIFFERENT_FUNCTION|La siguiente instrucción no está asociada con cualquier marco de la pila.|  
|E_CANNOT_SET_NEXT_STATEMENT_ON_EXCEPTION|Algunos motores de depuración no pueden establecer la siguiente instrucción después de una excepción.|  
  
## <a name="remarks"></a>Comentarios  
 El puntero de instrucción indica la siguiente instrucción o instrucción para ejecutar. Este método se utiliza para volver a intentar una línea de código fuente o para forzar la ejecución continúe en otra función, por ejemplo.  
  
## <a name="see-also"></a>Vea también  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)