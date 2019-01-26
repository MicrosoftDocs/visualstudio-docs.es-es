---
title: IDebugProgram2::Continue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::Continue
helpviewer_keywords:
- IDebugProgram2::Continue
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 225a1d78e3fb6610d9cbcebd1253131f0fe9caf2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55028548"
---
# <a name="idebugprogram2continue"></a>IDebugProgram2::Continue
Continúa ejecutando este programa desde un estado detenido. Se conserva ningún estado de ejecución anterior (por ejemplo, un paso), y el programa comienza a ejecutarse de nuevo.  
  
> [!NOTE]
>  Este método está obsoleto. Use la [continuar](../../../extensibility/debugger/reference/idebugprocess3-continue.md) método en su lugar.  
  
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
 [in] Un [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objeto que representa el subproceso.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Este método se llama en este programa, independientemente de cuántos programas se están depurando o programa que generó el evento de detención. La implementación debe conservar el estado de ejecución anterior (por ejemplo, un paso) y continuar la ejecución como si nunca había dejado antes de completar su ejecución anterior. Es decir, si un subproceso en este programa estaba haciendo una operación de paso y se detuvo porque otro programa se detiene y, a continuación, se llama a este método, el programa debe completar la operación de pasó por alto original.  
  
> [!WARNING]
>  No enviar un evento de detención o a un evento (sincrónico) inmediato [eventos](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) mientras se controla esta llamada; en caso contrario, el depurador puede dejar de responder.  
  
## <a name="see-also"></a>Vea también  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)