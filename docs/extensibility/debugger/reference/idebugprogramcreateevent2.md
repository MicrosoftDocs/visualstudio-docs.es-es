---
title: IDebugProgramCreateEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramCreateEvent2
helpviewer_keywords:
- IDebugProgramCreateEvent2 interface
ms.assetid: b19a7934-6179-4a68-9075-bd7dcd640b05
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5b73deab28f08ed9268033e941b64b753f64adf5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891025"
---
# <a name="idebugprogramcreateevent2"></a>IDebugProgramCreateEvent2
El motor DE depuración (DE) envía esta interfaz al administrador de depuración de la sesión (SDM) cuando un programa está asociado a.

## <a name="syntax"></a>Sintaxis

```
IDebugProgramCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El DE o el proveedor del puerto personalizado implementa esta interfaz para informar de que se ha creado un programa, normalmente en el momento en que se adjunta el programa. La interfaz [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) debe implementarse en el mismo objeto que esta interfaz. El SDM usa el `QueryInterface` método para tener acceso a la `IDebugEvent2` interfaz.

## <a name="notes-for-callers"></a>Notas para llamadores
 El DE o el proveedor del puerto personalizado crea y envía este objeto de evento para informar de la creación de un programa. El DE envía este evento mediante la función de devolución de llamada [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) proporcionada por el SDM cuando se adjunta al programa que se está depurando. El proveedor del puerto personalizado envía este evento mediante la interfaz [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) .

## <a name="remarks"></a>Notas
 El proveedor DE puerto personalizado o DE publica una nueva interfaz [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) llamando a [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md).

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
