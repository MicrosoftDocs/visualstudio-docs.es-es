---
title: IDebugEventCallback2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEventCallback2
helpviewer_keywords:
- IDebugEventCallback2
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a74825a955afdde03e63673c4b1b6afda5904953
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729889"
---
# <a name="idebugeventcallback2"></a>IDebugEventCallback2
Esta interfaz es utilizada por el motor de depuración (DE) para enviar los eventos del debug al administrador del debug de la sesión (SDM).

## <a name="syntax"></a>Sintaxis

```
IDebugEventCallback2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]implementa esta interfaz para recibir eventos de un motor de depuración.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 Un motor de depuración recibe normalmente esta interfaz cuando las llamadas SDM [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)o [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md). Un motor de depuración envía eventos al SDM llamando al [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente `IDebugEventCallback2`se muestran los métodos de .

|Método|Descripción|
|------------|-----------------|
|[Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|Envía una notificación de eventos de depuración al SDM.|

## <a name="remarks"></a>Observaciones
 Aunque [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) y [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) especifican `IDebugEventCallback2` que toman una interfaz, este no es el caso y el puntero de interfaz siempre será un valor nulo. En su lugar, el `IDebugEventCallback2` motor de depuración debe utilizar la interfaz recibida en la llamada a [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)o [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).

 Si un paquete implementa [IDebugEventCallback](../../../extensibility/debugger/reference/idebugeventcallback2.md) en código administrado, se recomienda encarecidamente que <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> se invoque en las distintas interfaces que se pasan a [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
