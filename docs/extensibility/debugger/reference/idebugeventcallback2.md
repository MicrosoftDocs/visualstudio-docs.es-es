---
title: IDebugEventCallback2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEventCallback2
helpviewer_keywords:
- IDebugEventCallback2
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d8d05ea232513a161b3123e08a20bc0f5b312b89
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56686930"
---
# <a name="idebugeventcallback2"></a>IDebugEventCallback2
Esta interfaz se utiliza el motor de depuración (DE) para enviar eventos de depuración para el Administrador de depuración de la sesión (SDM).

## <a name="syntax"></a>Sintaxis

```
IDebugEventCallback2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] implementa esta interfaz para recibir eventos de un motor de depuración.

## <a name="notes-for-callers"></a>Notas para los llamadores
 Un motor de depuración normalmente recibe esta interfaz cuando se llama el SDM [adjuntar](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [adjuntar](../../../extensibility/debugger/reference/idebugengine2-attach.md), o [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md). Un motor de depuración envía eventos al SDM mediante una llamada a [eventos](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 La tabla siguiente muestran los métodos de `IDebugEventCallback2`.

|Método|Descripción|
|------------|-----------------|
|[Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|Envía una notificación de eventos para el SDM la depuración.|

## <a name="remarks"></a>Comentarios
 Aunque [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) y [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) especificar que llevan una `IDebugEventCallback2` interfaz, esto no es el caso, y el puntero de interfaz siempre será un valor null. En su lugar, debe usar el motor de depuración del `IDebugEventCallback2` interfaz recibidos en la llamada a [adjuntar](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [adjuntar](../../../extensibility/debugger/reference/idebugengine2-attach.md), o [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).

 Si implementa un paquete [IDebugEventCallback](../../../extensibility/debugger/reference/idebugeventcallback2.md) en código administrado, es muy recomendable que <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> invocarse en las distintas interfaces que se pasan a [eventos](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [Asociar](../../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [Asociar](../../../extensibility/debugger/reference/idebugengine2-attach.md)