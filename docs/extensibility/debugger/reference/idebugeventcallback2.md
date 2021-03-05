---
description: El motor DE depuración (DE) utiliza esta interfaz para enviar eventos de depuración al administrador de depuración de sesión (SDM).
title: IDebugEventCallback2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEventCallback2
helpviewer_keywords:
- IDebugEventCallback2
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cb33bcbdff14b0f95aab5d8f300473c13d4c342f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152915"
---
# <a name="idebugeventcallback2"></a>IDebugEventCallback2
El motor DE depuración (DE) utiliza esta interfaz para enviar eventos de depuración al administrador de depuración de sesión (SDM).

## <a name="syntax"></a>Syntax

```
IDebugEventCallback2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] implementa esta interfaz para recibir eventos de un motor de depuración.

## <a name="notes-for-callers"></a>Notas para llamadores
 Normalmente, un motor de depuración recibe esta interfaz cuando el SDM llama a [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)o [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md). Un motor de depuración envía eventos al SDM mediante una llamada al [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IDebugEventCallback2` .

|Método|Descripción|
|------------|-----------------|
|[Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|Envía la notificación de eventos de depuración al SDM.|

## <a name="remarks"></a>Observaciones
 Aunque [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) y [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) especifican que toman una `IDebugEventCallback2` interfaz, este no es el caso y el puntero de interfaz siempre será un valor null. En su lugar, el motor de depuración debe usar la `IDebugEventCallback2` interfaz recibida en la llamada para [adjuntar](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [adjuntar](../../../extensibility/debugger/reference/idebugengine2-attach.md)o [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).

 Si un paquete implementa [IDebugEventCallback](../../../extensibility/debugger/reference/idebugeventcallback2.md) en código administrado, se recomienda que <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> se invoque en las diversas interfaces que se pasan al [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [Adjuntar](../../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [Adjuntar](../../../extensibility/debugger/reference/idebugengine2-attach.md)
