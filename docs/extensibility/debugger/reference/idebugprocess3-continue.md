---
title: IDebugProcess3::Continue | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProcess3::Continue
helpviewer_keywords:
- IDebugProcess3::Continue
ms.assetid: 57506242-5763-4c08-adb9-8a78ce02cebb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4c417998ab9c73ae2b52e297caa9de3dc9874f69
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53947704"
---
# <a name="idebugprocess3continue"></a>IDebugProcess3::Continue
Continúa la ejecución de este proceso de un estado detenido. Se conserva ningún estado de ejecución anterior (por ejemplo, un paso), y el proceso comienza a ejecutarse de nuevo.  
  
> [!NOTE]
>  Este método debería usarse en lugar de [continuar](../../../extensibility/debugger/reference/idebugprogram2-continue.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT Continue(  
   IDebugThread2* pThread  
);  
```  
  
```csharp  
int Continue(  
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pThread`  
 [in] Un [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objeto que representa el subproceso se puede continuar.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve el código de error.  
  
## <a name="remarks"></a>Comentarios  
 Este método se llama en este proceso, independientemente de cuántos procesos se están depurando o proceso que generó el evento de detención. La implementación debe conservar el estado de ejecución anterior (por ejemplo, un paso) y continuar la ejecución como si nunca había dejado antes de completar su ejecución anterior. Es decir, si un subproceso en este proceso estaba realizando una operación de paso y se detuvo porque se detuvo de algún otro proceso y, a continuación, `Continue` llamó, el subproceso debe completar la operación pasó por alto original.  
  
 **Advertencia** no enviar ningún evento de detención o a un evento (sincrónico) inmediato [eventos](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) mientras se controla esta llamada; en caso contrario, el depurador puede dejar de responder.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)