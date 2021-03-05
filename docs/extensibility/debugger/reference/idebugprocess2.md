---
description: Esta interfaz representa un proceso que se ejecuta en un puerto.
title: IDebugProcess2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2
helpviewer_keywords:
- IDebugProcess2 interface
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 131eacba321bac70c75b77faf33b18aae0135e55
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150268"
---
# <a name="idebugprocess2"></a>IDebugProcess2
Esta interfaz representa un proceso que se ejecuta en un puerto. Si el puerto es el local, `IDebugProcess2` normalmente representa un proceso físico en el equipo local.

## <a name="syntax"></a>Syntax

```
IDebugProcess2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Esta interfaz la implementa un proveedor de Puerto personalizado para administrar programas como un grupo. Esta interfaz debe ser implementada por el proveedor del puerto.

 Un motor de depuración también implementa esta interfaz si admite el inicio de un programa a través de [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).

## <a name="notes-for-callers"></a>Notas para llamadores
 El administrador de depuración de sesión (SDM) llama principalmente a esta interfaz para interactuar con un grupo de programas identificados en este proceso.

 Llame a [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md) o a [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md) para obtener esta interfaz. Esta interfaz también se devuelve mediante una llamada a `IDebugEngineLaunch2::LaunchSuspended` .

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IDebugProcess2` .

|Método|Descripción|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|Obtiene una descripción del proceso.|
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|Enumera los programas incluidos en este proceso.|
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|Obtiene el título, el nombre descriptivo o el nombre de archivo del proceso.|
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|Obtiene la instancia de un servidor de equipo en el que se ejecuta este proceso.|
|[Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)|Finaliza el proceso.|
|[Adjuntar](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|Se asocia al proceso.|
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|Determina si el SDM puede desasociar el proceso.|
|[Separar](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|Desasocia el depurador del proceso.|
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|Obtiene el identificador de proceso del sistema.|
|[Getprocessid (](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|Obtiene un identificador único global para este proceso.|
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> EN desuso|Obtiene el nombre de la sesión que está depurando el proceso.<br /><br /> En desuso. SIEMPRE debe devolver `E_NOTIMPL` .]|
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|Enumera los subprocesos que se ejecutan en el proceso.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|Solicita que se detenga el siguiente programa que ejecuta código en este proceso.|
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|Obtiene el puerto en el que se está ejecutando este proceso.|

## <a name="remarks"></a>Observaciones
 Un `IDebugProcess2` contiene una o más interfaces [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) .

## <a name="requirements"></a>Requisitos
 Encabezado: Msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)
- [Siguiente](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)
- [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
