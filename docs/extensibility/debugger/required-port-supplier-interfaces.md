---
title: Interfaces de proveedor de puertos | Microsoft Docs
description: Obtenga información sobre las interfaces que debe ejecutar un proveedor de puertos. Un proveedor de puertos proporciona puertos y los implementa.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- port suppliers, required interfaces
- debugging [Debugging SDK], port suppliers
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 96cf70302839a9de3c5fb0fec01136d9700ee17e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902376"
---
# <a name="required-port-supplier-interfaces"></a>Interfaces de proveedor de puertos necesarias
Un proveedor de puertos debe implementar la [interfaz IDebugPortSupplier2.](../../extensibility/debugger/reference/idebugportsupplier2.md) [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)

 Un proveedor de puertos proporciona puertos y los implementa. Por lo tanto, debe ejecutar las interfaces siguientes:

- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)

  Describe el puerto y enumera todos los procesos que se ejecutan en el puerto.

- [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)

  Proporciona para iniciar y finalizar procesos en el puerto.

- [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)

  Proporciona un mecanismo para que los programas que se ejecutan en el contexto de este puerto le notifiquen la creación y destrucción del nodo del programa. Para obtener más información, vea [Nodos de programa](../../extensibility/debugger/program-nodes.md).

- `IConnectionPointContainer`

  Proporciona un punto de conexión [para IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md).

## <a name="port-supplier-operation"></a>Operación de proveedor de puertos
 El [receptor IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) recibe notificaciones cuando se crean procesos y programas y se destruyen en un puerto. Se requiere un puerto para enviar [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) cuando se crea un proceso e [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) cuando se destruye un proceso en el puerto. También se requiere un puerto para enviar [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) cuando se crea un programa e [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) cuando se destruye un programa en un proceso que se ejecuta en el puerto.

 Normalmente, un puerto envía eventos de creación y destrucción del programa en respuesta a los [métodos AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) y [RemoveProgramNode,](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) respectivamente.

 Dado que un puerto puede iniciar y finalizar procesos físicos y programas lógicos, el motor de depuración también debe implementar las interfaces siguientes:

- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)

  Describe el proceso físico. Se deben implementar al menos los métodos siguientes:

  - [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)

  - [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)

  - [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)

  - [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)

  - [GetProcessId](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)

  - [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)

- [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)

  Proporciona una manera de que el SDM se adjunte y se desasoje de un proceso.

- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)

  Describe el programa lógico. Se deben implementar al menos los métodos siguientes:

  - [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)

  - [GetProcess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)

  - [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)

- [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)

  Proporciona una manera de que el SDM se adjunte a este programa.

## <a name="see-also"></a>Consulta también
- [Implementación de un proveedor de puertos](../../extensibility/debugger/implementing-a-port-supplier.md)
