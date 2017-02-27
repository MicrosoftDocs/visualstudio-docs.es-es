---
title: "IDebugEngine2::ContinueFromSynchronousEvent | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine2::ContinueFromSynchronousEvent"
helpviewer_keywords: 
  - "IDebugEngine2::ContinueFromSynchronousEvent"
ms.assetid: 9a57dfcd-df8e-4be5-b1fe-bd853e3c6bb2
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugEngine2::ContinueFromSynchronousEvent
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Llamado por el administrador de depuración de la sesión \(SDM\) para indicar que un evento sincrónico de depuración, incluido previamente por el motor de depuración al \(DE\) SDM, se recibió y procesado.  
  
## Sintaxis  
  
```cpp#  
HRESULT ContinueFromSynchronousEvent(   
   IDebugEvent2* pEvent  
);  
```  
  
```c#  
HRESULT ContinueFromSynchronousEvent(   
   IDebugEvent2 pEvent  
);  
```  
  
#### Parámetros  
 `pEvent`  
 \[in\]  Un objeto de [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) que representa el evento sincrónico previamente enviado desde que el depurador ahora debe continuar.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 El OF debe comprobar que fuera el origen del evento representado por el parámetro de `pEvent` .  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo implementar este método para un objeto simple de `CEngine` que implemente la interfaz de [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) .  
  
```cpp#  
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
  
## Vea también  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)