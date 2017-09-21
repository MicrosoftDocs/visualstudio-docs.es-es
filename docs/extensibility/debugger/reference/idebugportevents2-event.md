---
title: "IDebugPortEvents2::Event | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortEvents2::Event"
helpviewer_keywords: 
  - "IDebugPortEvents2::Event"
ms.assetid: 5cc813f7-04a1-4462-9ea7-fbddcf0e0143
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# IDebugPortEvents2::Event
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Este método envía los eventos que implican la creación y destrucción de procesos y de programas en un puerto.  
  
## Sintaxis  
  
```cpp#  
HRESULT Event(  
   IDebugCoreServer2* pServer,  
   IDebugPort2*       pPort,  
   IDebugProcess2*    pProcess,  
   IDebugProgram2*    pProgram,  
   IDebugEvent2*      pEvent,  
   REFIID             riidEvent  
);  
```  
  
```c#  
int Event(  
   IDebugCoreServer2 pServer,   
   IDebugPort2       pPort,   
   IDebugProcess2    pProcess,   
   IDebugProgram2    pProgram,   
   IDebugEvent2      pEvent,   
   ref Guid          riidEvent  
);  
```  
  
#### Parámetros  
 `pMachine`  
 \[in\]  Un objeto de [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) que representa el servidor de depuración \(hay uno para cada instancia de [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]\) donde se produjo el evento.  
  
 `pPort`  
 \[in\]  Un objeto de [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) que representa el puerto en el que se produjo el evento.  
  
 `pProcess`  
 \[in\]  Un objeto de [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) que representa el proceso en el que se produjo el evento.  
  
 `pProgram`  
 \[in\]  Un objeto de [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) que representa el programa en la que se produjo el evento.  
  
 `pEvent`  
 \[in\]  un objeto de [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) que identifica el evento.  Los posibles eventos son los siguientes:  
  
-   [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)  
  
-   [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)  
  
-   [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)  
  
-   [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)  
  
 `riidEvent`  
 \[in\]  GUID del evento.  Dado que el evento se convierte en [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) antes de llamar a este método, este identificador facilita determinar se está publicando el evento.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)   
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)