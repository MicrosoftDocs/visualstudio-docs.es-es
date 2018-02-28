---
title: IDebugExceptionEvent2::CanPassToDebuggee | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 3a443b3f88ec64d24ea7a5bf4db682e5aa10b2eb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
Determina si se permite o no el motor de depuración (Alemania) es compatible con la opción de pasar esta excepción al programa que se está depurando cuando se reanuda la ejecución.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT CanPassToDebuggee(  
   void  
);  
```  
  
```csharp  
int CanPassToDebuggee();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` (la excepción puede pasarse al programa) o `S_FALSE` (la excepción no se pueden pasar).  
  
## <a name="remarks"></a>Comentarios  
 La DE debe tener una acción predeterminada para pasar al lado depurado. Puede recibir el IDE la [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) eventos y llame al método el [continuar](../../../extensibility/debugger/reference/idebugprocess3-continue.md) método sin llamar a la `CanPassToDebuggee` método. Por lo tanto, la DE debe tener un caso predeterminado para pasar la excepción o no.  
  
## <a name="see-also"></a>Vea también  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)