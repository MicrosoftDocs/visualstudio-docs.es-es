---
title: "Orígenes de eventos (Visual Studio SDK) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], event sources
ms.assetid: b9ba0908-ae4c-4a64-aab1-bee453dd7a22
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fd6acee81b2202500c9d84f5920cd4f1019a3b2d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="event-sources-visual-studio-sdk"></a>Orígenes de eventos (SDK de Visual Studio)
Hay dos orígenes de eventos: el motor de depuración (Alemania) y la sesión de depuración de administrador (SDM). Eventos enviados desde un Alemania tienen un motor distinto de NULL, mientras que eventos enviados desde el SDM tienen un motor NULL.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo enviar la **IDebugProgramCreateEvent2** desde el DE para el SDM.  
  
```  
CDebugProgramCreateEvent* pProgramCreateEvent = new CDebugProgramCreateEvent();  
if (FAILED(pCallback->Event(m_pEngine, NULL, m_pProgram, NULL, pProgramCreateEvent, IID_IDebugProgramCreateEvent2, EVENT_ASYNCHRONOUS)))  
{  
   // Handle failure here.  
}  
]  
  
CEvent * pProgCreate = new CEvent(IID_IDebugProgramCreateEvent2, EVENT_ASYNCHRONOUS);    
pProgCreate->SendEvent(pCallback, m_pEngine, (IDebugProgram2 *)this, NULL);  
  
HRESULT CEvent::SendEvent(IDebugEventCallback2 *pCallback, IDebugEngine2 *pEngine, IDebugProgram2 *pProgram, IDebugThread2 *pThread) {    
   HRESULT hr;    
  
   if (m_dwAttrib & EVENT_STOPPING)    
   {    
      hr = SendStoppingEvent(pCallback, pEngine, pProgram, pThread);    
   }    
   else if (m_dwAttrib & EVENT_SYNCHRONOUS)    
   {    
      hr = SendSynchronousEvent(pCallback, pEngine, pProgram, pThread);    
   }    
   else    
   {    
      assert(m_dwAttrib == 0);    
      hr = SendAsynchronousEvent(pCallback, pEngine, pProgram, pThread);    
   }    
  
   return hr;    
}    
  
HRESULT CEvent::SendAsynchronousEvent(IDebugEventCallback2 *pCallback, IDebugEngine2 *pEngine, IDebugProgram2 *pProgram, IDebugThread2 *pThread) {    
  
    HRESULT hr;    
  
   // Make sure the CEvent object running this code is not deleted until the code completes.    
   AddRef();    
  
   pCallback->Event(pEngine, NULL, pProgram, pThread, (IDebugEvent2 *)this, m_riid, m_dwAttrib);    
  
   // No error recovery here.    
   hr = S_OK;     
  
   Release();    
   return hr;    
}  
  
```  
  
## <a name="see-also"></a>Vea también  
 [Envío de eventos](../../extensibility/debugger/sending-events.md)