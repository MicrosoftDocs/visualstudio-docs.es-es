---
title: IDebugExceptionEvent2::CanPassToDebuggee | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords: IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ef10fd3ca7f41c2afd1c827fb71ca2178782e3d4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
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