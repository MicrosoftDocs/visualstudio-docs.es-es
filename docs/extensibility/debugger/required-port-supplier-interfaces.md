---
title: "Interfaces de proveedor de puerto requerido | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "proveedores de puertos, interfaces necesarias"
  - "depurar [SDK de depuración], proveedores de puerto"
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Interfaces de proveedor de puerto requerido
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un proveedor de puerto debe implementar la interfaz de [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) .       [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)  
  
 Dado que los puertos de fuentes de un proveedor de puerto, debe también implementarlas.  Por consiguiente, debe implementar las siguientes interfaces:  
  
-   [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)  
  
     describe el puerto y puede enumerar todos los procesos que se ejecutan en el puerto.  
  
-   [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)  
  
     Para iniciar y finalizar procesos en el puerto.  
  
-   [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)  
  
     Proporciona un mecanismo para programas que se ejecutan dentro del contexto de este puerto para notificarlo de creación y destrucción de nodo del programa.  Para obtener más información, vea [Nodos de programa](../../extensibility/debugger/program-nodes.md).  
  
-   `IConnectionPointContainer`  
  
     proporciona un punto de conexión para [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md).  
  
## Operación de proveedor de puerto  
 El receptor de [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) recibe notificaciones cuando el proceso y programas se crean y se destruyen en un puerto.  un puerto se requiere para enviar [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) cuando se crea un proceso y [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) cuando un proceso se destruye en el puerto.  Un puerto también se requiere para enviar [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) cuando se crea un programa y [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) cuando un programa se destruye en un proceso en el puerto.  
  
 Un puerto envía normalmente el programa crea y destruye eventos en respuesta a los métodos de [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) y de [RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) , respectivamente.  
  
 Dado que un puerto puede iniciar y finalizar procesos físicos y los programas lógicos, estas interfaces debe implementar también por el motor de depuración:  
  
-   [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)  
  
     describe el proceso físico.  Al menos los siguientes métodos deben implementarse:  
  
    -   [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)  
  
    -   [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)  
  
    -   [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)  
  
    -   [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)  
  
    -   [GetProcessId](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)  
  
    -   [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)  
  
-   [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)  
  
     proporciona una manera para que el SDM adjunte y se desasocie de un proceso.  
  
-   [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)  
  
     describe el programa lógico.  Al menos los siguientes métodos deben implementarse:  
  
    -   [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)  
  
    -   [GetProcess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)  
  
    -   [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)  
  
-   [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)  
  
     Proporciona una manera para el SDM a la asociación a este programa.  
  
## Vea también  
 [Implementar un proveedor de puerto](../../extensibility/debugger/implementing-a-port-supplier.md)