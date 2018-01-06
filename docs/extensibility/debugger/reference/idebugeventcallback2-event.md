---
title: IDebugEventCallback2::Event | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEventCallback2::Event
helpviewer_keywords: IDebugEventCallback2::Event
ms.assetid: e5a3345b-d460-4e40-8f5b-3111c56a2ed9
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0a7e5d4d20ae7e4409599a77250986b759f152fb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugeventcallback2event"></a>IDebugEventCallback2::Event
Envía una notificación de eventos de depuración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT Event(   
   IDebugEngine2*  pEngine,  
   IDebugProcess2* pProcess,  
   IDebugProgram2* pProgram,  
   IDebugThread2*  pThread,  
   IDebugEvent2*   pEvent,  
   REFIID          riidEvent,  
   DWORD           dwAttrib  
);  
```  
  
```csharp  
int Event(   
   IDebugEngine2  pEngine,  
   IDebugProcess2 pProcess,  
   IDebugProgram2 pProgram,  
   IDebugThread2  pThread,  
   IDebugEvent2   pEvent,  
   ref Guid       riidEvent,  
   uint           dwAttrib  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pEngine`  
 [in] Un [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) objeto que representa el motor de depuración (Alemania) que está enviando este evento. Es necesario un Alemania para rellenar este parámetro.  
  
 `pProcess`  
 [in] Un [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) objeto que representa el proceso en el que se produce el evento. Este parámetro se rellena mediante el Administrador de sesión de depuración (SDM). Un Alemania siempre transfiere un valor null para este parámetro.  
  
 `pProgram`  
 [in] Un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objeto que representa el programa en el que se produce este evento. Para la mayoría de los eventos, este parámetro no es un valor null.  
  
 `pThread`  
 [in] Un [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objeto que representa el subproceso en el que se produce este evento. Para los eventos de parada, este parámetro no puede ser un valor null como el marco de pila se obtiene de este parámetro.  
  
 `pEvent`  
 [in] Un [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) objeto que representa el evento de depuración.  
  
 `riidEvent`  
 [in] GUID que identifica la interfaz de eventos que se obtiene de la `pEvent` parámetro.  
  
 `dwAttrib`  
 [in] Una combinación de indicadores de la [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) enumeración.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Cuando se llama a este método, el `dwAttrib` parámetro debe coincidir con el valor devuelto de la [GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md) pasa el método que llama en el objeto de evento en el `pEvent` parámetro.  
  
 Todos los eventos de depuración se registran de forma asincrónica, independientemente de si un evento es asincrónico o no. Cuando un Alemania llama a este método, el valor devuelto no indica si el evento se ha procesado, solo si se ha recibido el evento. De hecho, en la mayoría de los casos, el evento no ha procesado cuando este método devuelve.  
  
## <a name="see-also"></a>Vea también  
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)