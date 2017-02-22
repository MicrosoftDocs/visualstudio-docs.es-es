---
title: "IDebugEventCallback2::Event | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEventCallback2::Event"
helpviewer_keywords: 
  - "IDebugEventCallback2::Event"
ms.assetid: e5a3345b-d460-4e40-8f5b-3111c56a2ed9
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEventCallback2::Event
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Envía la notificación de eventos de depuración.  
  
## Sintaxis  
  
```cpp#  
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
  
```c#  
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
  
#### Parámetros  
 `pEngine`  
 \[in\]  Un objeto de [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) que representa el motor de depuración \(DE\) que está enviando este evento.  Un OF se necesita para completar este parámetro.  
  
 `pProcess`  
 \[in\]  Un objeto de [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) que representa el proceso en el que el evento.  Este parámetro es completo por el administrador de depuración de la sesión \(SDM\).  Un OF pasa siempre un valor NULL para este parámetro.  
  
 `pProgram`  
 \[in\]  Un objeto de [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) que representa el programa en el que este evento.  Para la mayoría de los eventos, este parámetro no es un valor null.  
  
 `pThread`  
 \[in\]  Un objeto de [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) que representa el subproceso en el que este evento.  Para detener eventos, este parámetro no puede ser un valor NULL cuando el marco de pila se obtiene de este parámetro.  
  
 `pEvent`  
 \[in\]  Un objeto de [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) que representa el evento de depuración.  
  
 `riidEvent`  
 \[in\]  GUID que identifica qué interfaz de eventos a obtener el parámetro de `pEvent` .  
  
 `dwAttrib`  
 \[in\]  Una combinación de marcadores de enumeración de [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) .  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Al llamar a este método, el parámetro de `dwAttrib` debe coincidir con el valor devuelto del método de [GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md) como llamada si el objeto de evento pasado en el parámetro de `pEvent` .  
  
 Todos los eventos de depuración se envían de forma asincrónica, sin importar si un evento es asincrónico o no.  Cuando un OF llama a este método, el valor devuelto no indica si el evento se procesó, sólo si el evento se recibido.  De hecho, en la mayoría de los casos, el evento no se ha procesado cuando este método devuelve.  
  
## Vea también  
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)