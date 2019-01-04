---
title: IDebugEngine2::ContinueFromSynchronousEvent | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEngine2::ContinueFromSynchronousEvent
helpviewer_keywords:
- IDebugEngine2::ContinueFromSynchronousEvent
ms.assetid: 9a57dfcd-df8e-4be5-b1fe-bd853e3c6bb2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: eaa1d399de86864eb8d1c20e6b8e085a2e0d9f9f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53849459"
---
# <a name="idebugengine2continuefromsynchronousevent"></a>IDebugEngine2::ContinueFromSynchronousEvent
Llamado por el Administrador de depuración de la sesión (SDM) para indicar que un evento de depuración sincrónica, enviado previamente por el motor de depuración (DE) para el SDM, se ha recibido y procesado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT ContinueFromSynchronousEvent(   
   IDebugEvent2* pEvent  
);  
```  
  
```csharp  
HRESULT ContinueFromSynchronousEvent(   
   IDebugEvent2 pEvent  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pEvent`  
 [in] Un [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) objeto que representa los eventos sincrónicos enviados anteriormente desde el que el depurador ahora debe seguir.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Debe comprobar la DE que era el origen del evento representado por la `pEvent` parámetro.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra cómo implementar este método para una sencilla `CEngine` objeto que implementa el [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) interfaz.  
  
```cpp  
HRESULT CEngine::ContinueFromSynchronousEvent(IDebugEvent2* pEvent)  
{  
   HRESULT hr;  
  
   // Create a pointer to a unique event interface defined for batch file  
   // breaks.    
   IAmABatchFileEvent *pBatEvent;  
   // Check for successful query for the unique batch file event  
   // interface.  
   if (SUCCEEDED(pEvent->QueryInterface(IID_IAmABatchFileEvent,  
                                       (void **)&pBatEvent)))  
   {  
      // Release the result of the QI.  
      pBatEvent->Release();  
      // Check thread message for notification to continue.  
      if (PostThreadMessage(GetCurrentThreadId(),  
                            WM_CONTINUE_SYNC_EVENT,  
                            0,  
                            0))  
      {    
         hr = S_OK;  
      }  
      else  
      {  
         hr = HRESULT_FROM_WIN32(GetLastError());  
      }  
   }  
   else  
   {  
      hr = E_INVALIDARG;  
   }  
   return hr;  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)