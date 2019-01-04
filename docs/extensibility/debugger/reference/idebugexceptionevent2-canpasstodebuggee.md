---
title: IDebugExceptionEvent2::CanPassToDebuggee | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6c4b0112c972c5521abc1007ad98259fae145769
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53822815"
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
Determina si el motor de depuración (DE) es compatible con la opción de pasar esta excepción al programa que se está depurando cuando se reanuda la ejecución.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT CanPassToDebuggee(  
   void  
);  
```  
  
```csharp  
int CanPassToDebuggee();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve una `S_OK` (la excepción puede pasarse al programa) o `S_FALSE` (la excepción no se pueden pasar).  
  
## <a name="remarks"></a>Comentarios  
 La DE debe tener una acción predeterminada para pasar al lado depurado. El IDE puede recibir el [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) evento y llamar a la [continuar](../../../extensibility/debugger/reference/idebugprocess3-continue.md) método sin llamar a la `CanPassToDebuggee` método. Por lo tanto, la DE debe tener un caso predeterminado para pasar la excepción o no.  
  
## <a name="see-also"></a>Vea también  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)