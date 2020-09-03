---
title: Interfaces de proveedor de Puerto requeridas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- port suppliers, required interfaces
- debugging [Debugging SDK], port suppliers
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a065389a6b9b67b8bce82394569ce65afb0f8d55
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "67821431"
---
# <a name="required-port-supplier-interfaces"></a>Interfaces de proveedor de puertos requeridas
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un proveedor de puerto debe implementar la interfaz [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) . [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)  
  
 Dado que un proveedor de Puerto proporciona puertos, también debe implementarlos. Por lo tanto, debe implementar las siguientes interfaces:  
  
- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)  
  
     Describe el puerto y puede enumerar todos los procesos que se ejecutan en el puerto.  
  
- [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)  
  
     Proporciona para iniciar y finalizar procesos en el puerto.  
  
- [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)  
  
     Proporciona un mecanismo para que los programas que se ejecutan en el contexto de este puerto notifiquen la creación y destrucción del nodo del programa. Para obtener más información, vea [nodos de programa](../../extensibility/debugger/program-nodes.md).  
  
- `IConnectionPointContainer`  
  
     Proporciona un punto de conexión para [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md).  
  
## <a name="port-supplier-operation"></a>Operación de proveedor de Puerto  
 El receptor [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) recibe notificaciones cuando se crean y se destruyen procesos y programas en un puerto. Se requiere un puerto para enviar [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) cuando se crea un proceso y [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) cuando se destruye un proceso en el puerto. También se necesita un puerto para enviar [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) cuando se crea un programa y [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) cuando se destruye un programa en un proceso que se ejecuta en el puerto.  
  
 Normalmente, un puerto envía eventos de creación y destrucción de programas en respuesta a los métodos [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) y [RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) , respectivamente.  
  
 Dado que un puerto puede iniciar y finalizar procesos físicos y programas lógicos, el motor de depuración también debe implementar estas interfaces:  
  
- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)  
  
  Describe el proceso físico. Se deben implementar al menos los siguientes métodos:  

  - [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)  

  - [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)  

  - [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)  

  - [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)  

  - [Getprocessid (](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)  

  - [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)  

- [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)  
  
    Proporciona una manera para que el SDM se adjunte y se desasocie de un proceso.  
  
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)  
  
  Describe el programa lógico. Se deben implementar al menos los siguientes métodos:  

  - [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)  

  - [GetProcess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)  

  - [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)  
  
- [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)  
  
     Proporciona una manera para que el SDM se adjunte a este programa.  
  
## <a name="see-also"></a>Consulte también  
 [Implementación de un proveedor de puertos](../../extensibility/debugger/implementing-a-port-supplier.md)
