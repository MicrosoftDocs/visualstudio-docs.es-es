---
title: Interfaces de proveedor de puerto necesarias | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- port suppliers, required interfaces
- debugging [Debugging SDK], port suppliers
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 251b5c9d96ac7d0e82705c81b1b568e2d85b88f6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49248194"
---
# <a name="required-port-supplier-interfaces"></a>Interfaces de proveedor de puertos requeridas
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Debe implementar un proveedor de puerto del [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) interfaz.[ IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)  
  
 Dado que un proveedor de puerto proporciona puertos, también debe implementarlos. Por lo tanto, deben implementar las interfaces siguientes:  
  
-   [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)  
  
     Describe el puerto y puede enumerar todos los procesos que se ejecutan en el puerto.  
  
-   [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)  
  
     Se proporciona para iniciar y terminar procesos en el puerto.  
  
-   [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)  
  
     Proporciona un mecanismo para programas que se ejecutan dentro del contexto de este puerto para notificarle de destrucción y la creación del nodo de programa. Para obtener más información, consulte [programa nodos](../../extensibility/debugger/program-nodes.md).  
  
-   `IConnectionPointContainer`  
  
     Proporciona un punto de conexión para [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md).  
  
## <a name="port-supplier-operation"></a>Operación de proveedor de puerto  
 El [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) receptor recibe notificaciones cuando el proceso y programas se crean y destruyen en un puerto. Se requiere un puerto para enviar [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) cuando se crea un proceso y [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) cuando se destruye un proceso en el puerto. También es necesario un puerto de envío [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) cuando se crea un programa y [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) cuando se destruye un programa en un proceso que se ejecuta en el puerto.  
  
 Un puerto normalmente envía programa crear y destruir eventos en respuesta a la [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) y [RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) métodos, respectivamente.  
  
 Dado que un puerto puede iniciar y finalizar los procesos físicos y lógicos programas, estas interfaces también deben implementarse mediante el motor de depuración:  
  
-   [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)  
  
     Describe el proceso físico. Al menos se deben implementar los métodos siguientes:  
  
    -   [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)  
  
    -   [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)  
  
    -   [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)  
  
    -   [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)  
  
    -   [GetProcessId](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)  
  
    -   [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)  
  
-   [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)  
  
     Proporciona una forma para el SDM asociar y desasociar propio de un proceso.  
  
-   [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)  
  
     Describe el sistema lógico. Al menos se deben implementar los métodos siguientes:  
  
    -   [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)  
  
    -   [GetProcess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)  
  
    -   [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)  
  
-   [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)  
  
     Proporciona una forma para el SDM adjuntar a este programa.  
  
## <a name="see-also"></a>Vea también  
 [Implementación de un proveedor de puerto](../../extensibility/debugger/implementing-a-port-supplier.md)

