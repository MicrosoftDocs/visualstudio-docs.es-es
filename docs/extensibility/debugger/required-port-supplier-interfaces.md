---
title: Interfaces de proveedores de puertos requeridas ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- port suppliers, required interfaces
- debugging [Debugging SDK], port suppliers
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf2aeb1f26f81d773e171aa3fed6b0f2ef976c91
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713152"
---
# <a name="required-port-supplier-interfaces"></a>Interfaces de proveedores de puertos requeridas
Un proveedor de puertos debe implementar el [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) interfaz. [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)

 Un proveedor de puertos suministra puertos y los implementa. Por lo tanto, debe ejecutar las siguientes interfaces:

- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)

  Describe el puerto y enumera todos los procesos que se ejecutan en el puerto.

- [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)

  Proporciona para iniciar y finalizar procesos en el puerto.

- [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)

  Proporciona un mecanismo para que los programas que se ejecutan dentro del contexto de este puerto le notifiquen la creación y destrucción de nodo de programa. Para obtener más información, consulte [Nodos de](../../extensibility/debugger/program-nodes.md)programa .

- `IConnectionPointContainer`

  Proporciona un punto de conexión para [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md).

## <a name="port-supplier-operation"></a>Operación de proveedores portuarios
 El receptor [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) recibe notificaciones cuando el proceso y los programas se crean y destruyen en un puerto. Se requiere un puerto para enviar [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) cuando se crea un proceso y [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) cuando se destruye un proceso en el puerto. También es necesario un puerto para enviar [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) cuando se crea un programa y [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) cuando se destruye un programa en un proceso que se ejecuta en el puerto.

 Normalmente, un puerto envía eventos de creación y destrucción de programas en respuesta a los métodos [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) y [RemoveProgramNode,](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) respectivamente.

 Dado que un puerto puede iniciar y terminar tanto los procesos físicos como los programas lógicos, el motor de depuración también debe implementar las siguientes interfaces:

- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)

  Describe el proceso físico. Al menos deben implementarse los siguientes métodos:

  - [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)

  - [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)

  - [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)

  - [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)

  - [GetProcessId](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)

  - [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)

- [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)

  Proporciona una manera para que el SDM se adjunte y se desvincule de un proceso.

- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)

  Describe el programa lógico. Al menos deben implementarse los siguientes métodos:

  - [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)

  - [GetProcess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)

  - [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)

- [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)

  Proporciona una manera para que el SDM se asocie a este programa.

## <a name="see-also"></a>Vea también
- [Implementación de un proveedor portuario](../../extensibility/debugger/implementing-a-port-supplier.md)
