---
title: IDebugThread2::SetNextStatement | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugThread2::SetNextStatement
helpviewer_keywords:
- IDebugThread2::SetNextStatement
ms.assetid: 9e2834dd-4ecf-45af-8e6c-f9318ebdac06
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e59d4087e44458ecd49efd5d7be9f45e68c6da2b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugthread2setnextstatement"></a>IDebugThread2::SetNextStatement
Establece el puntero de instrucción actual en el contexto de código especificada.  
  
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
 Reservado para uso futuro; establecer en un valor null.  
  
 `pCodeContext`  
 [in] Un [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) objeto que describe la ubicación del código va a ejecutar y su contexto.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error. La tabla siguiente muestran otros valores posibles.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|E_CANNOT_SET_NEXT_STATEMENT_ON_NONLEAF_FRAME|La siguiente instrucción no puede estar en un marco de pila más profundo en la pila de marco.|  
|E_CANNOT_SETIP_TO_DIFFERENT_FUNCTION|La siguiente instrucción que no está asociada con cualquier marco de la pila.|  
|E_CANNOT_SET_NEXT_STATEMENT_ON_EXCEPTION|Algunos motores de depuración no pueden establecer la siguiente instrucción después de una excepción.|  
  
## <a name="remarks"></a>Comentarios  
 El puntero de instrucción indica la siguiente instrucción o instrucción para ejecutar. Este método se utiliza para volver a intentar una línea de código fuente o para forzar la ejecución continúe en otra función, por ejemplo.  
  
## <a name="see-also"></a>Vea también  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)