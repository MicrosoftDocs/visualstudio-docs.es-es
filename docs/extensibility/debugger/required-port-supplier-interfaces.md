---
title: Interfaces de proveedor de puerto necesarias | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- port suppliers, required interfaces
- debugging [Debugging SDK], port suppliers
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 973d191305383967aee1c7379fd203375a71c825
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="required-port-supplier-interfaces"></a>Interfaces de proveedor de puerto requerido
Un proveedor de puerto debe implementar la [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) interfaz.[ IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)  
  
 Dado que un proveedor de puerto proporciona puertos, también debe implementarlos. Por lo tanto, debe implementar las interfaces siguientes:  
  
-   [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)  
  
     Describe el puerto y puede enumerar todos los procesos que se ejecutan en el puerto.  
  
-   [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)  
  
     Se proporciona para iniciar y detener procesos en el puerto.  
  
-   [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)  
  
     Proporciona un mecanismo para programas que se ejecutan en contexto de este puerto para notificarle del programa nodo creación y destrucción. Para obtener más información, consulte [programa nodos](../../extensibility/debugger/program-nodes.md).  
  
-   `IConnectionPointContainer`  
  
     Proporciona un punto de conexión para [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md).  
  
## <a name="port-supplier-operation"></a>Operación de proveedor de puerto  
 El [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) receptor recibe notificaciones cuando el proceso y programas se crean y destruyen en un puerto. Es necesario un puerto de envío [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) cuando se crea un proceso y [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) cuando se destruye un proceso en el puerto. También se necesita un puerto para enviar [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) cuando se crea un programa y [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) cuando se destruye un programa en un proceso que se ejecuta en el puerto.  
  
 Un puerto normalmente programa envía crear y destruir eventos en respuesta a la [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) y [RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) métodos, respectivamente.  
  
 Dado que un puerto puede iniciar y finalizar procesos físicos y lógicos programas, estas interfaces también deben implementarse mediante el motor de depuración:  
  
-   [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)  
  
     Describe el proceso físico. Al menos se deben implementar los métodos siguientes:  
  
    -   [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)  
  
    -   [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)  
  
    -   [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)  
  
    -   [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)  
  
    -   [GetProcessId](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)  
  
    -   [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)  
  
-   [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)  
  
     Proporciona una manera para que el SDM conectar y desconectar a sí mismo de un proceso.  
  
-   [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)  
  
     Describe el sistema lógico. Al menos se deben implementar los métodos siguientes:  
  
    -   [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)  
  
    -   [GetProcess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)  
  
    -   [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)  
  
-   [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)  
  
     Proporciona una manera para que el SDM adjuntar a este programa.  
  
## <a name="see-also"></a>Vea también  
 [Implementación de un proveedor de puerto](../../extensibility/debugger/implementing-a-port-supplier.md)