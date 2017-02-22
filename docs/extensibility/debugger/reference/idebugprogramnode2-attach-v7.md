---
title: "IDebugProgramNode2::Attach_V7 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramNode2::Attach"
helpviewer_keywords: 
  - "IDebugProgramNode2::Attach_V7"
  - "IDebugProgramNode2::Attach"
ms.assetid: b5ffc736-efc7-4ca8-964d-5536ff891b0e
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramNode2::Attach_V7
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

DESUSADO.  NOT UTILICE.  
  
## Sintaxis  
  
```cpp#  
HRESULT Attach_V7 (   
   IDebugProgram2*       pMDMProgram,  
   IDebugEventCallback2* pCallback,  
   DWORD                 dwReason  
);  
```  
  
```c#  
int Attach_V7 (   
   IDebugProgram2       pMDMProgram,  
   IDebugEventCallback2 pCallback,  
   uint                 dwReason  
);  
```  
  
#### Parámetros  
 `pMDMProgram`  
 \[in\]  La interfaz de [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) a la que representa el programa para adjuntar.  
  
 `pCallback`  
 \[in\]  La interfaz de [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) que se utilizará para enviar eventos de depuración al SDM.  
  
 `dwReason`  
 \[in\]  Un valor de enumeración de [ATTACH\_REASON](../../../extensibility/debugger/reference/attach-reason.md) que especifica la razón de asociar.  
  
## Valor devuelto  
 Una implementación siempre debe devolver `E_NOTIMPL`.  
  
## Comentarios  
  
> [!WARNING]
>  A partir de [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)], este método se utiliza y debe ya no devolver siempre `E_NOTIMPL`.  Vea la interfaz de [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) para un enfoque alternativo si el nodo de programa necesita indicar que no puede asociarse a o si el nodo de programa está estableciendo simplemente el programa `GUID`. si no, implemente el método de [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) .  
  
## antes de Visual Studio 2005  
 Este método debe ser implementado sólo si el OF se ejecuta en el espacio de direcciones del programa que se depura.  De lo contrario, este método debe devolver `S_FALSE`.  
  
 Cuando se llama a este método, el OF debería enviar el objeto de evento de [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) , si no se ha enviado aún para esta instancia de la interfaz de [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) , así como objetos de evento de [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) y de [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) .  El objeto de evento de [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) se envía si el parámetro de `dwReason` es `ATTACH_REASON_LAUNCH`.  
  
 El OF debe llamar al método de [GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) en el objeto de [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) proporcionado por el objeto de evento de [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) , y debe almacenar que el GUID del programa en los datos de la instancia del objeto de `IDebugProgram2` implementado por el OF.  
  
## Vea también  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)   
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)   
 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)   
 [ATTACH\_REASON](../../../extensibility/debugger/reference/attach-reason.md)