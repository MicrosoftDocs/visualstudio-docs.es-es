---
title: IDebugBreakpointBoundEvent2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointBoundEvent2
helpviewer_keywords:
- IDebugBreakpointBoundEvent2
ms.assetid: 24ba362e-5be1-481a-b071-e1ebd3cae6e8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7943addb4334710da3252a4d822330e45b6e0f80
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735302"
---
# <a name="idebugbreakpointboundevent2"></a>IDebugBreakpointBoundEvent2
Esta interfaz indica al administrador de depuración de sesión (SDM) que un punto de interrupción pendiente se ha enlazado correctamente a un programa cargado.

## <a name="syntax"></a>Sintaxis

```
IDebugBreakpointBoundEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El DE implementa esta interfaz como parte de su compatibilidad con puntos de interrupción. El [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaz debe implementarse en el mismo objeto que esta `IDebugEvent2` interfaz (el SDM utiliza [QueryInterface](/cpp/atl/queryinterface) para tener acceso a la interfaz).

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 El DE crea y envía este objeto de evento cuando un punto de interrupción pendiente se enlaza correctamente al programa que se está depurando. El evento se envía mediante la función de devolución de llamada [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) proporcionada por el SDM cuando se adjunta al programa que se está depurando.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente `IDebugBreakpointBoundEvent2`se muestran los métodos de .

|Método|Descripción|
|------------|-----------------|
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)|Obtiene el punto de interrupción pendiente que se está enlazando.|
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)|Crea un enumerador de puntos de interrupción enlazados en este evento.|

## <a name="remarks"></a>Observaciones
 Cada vez que se enlaza un punto de interrupción, se envía un evento al SDM. Si no se puede enlazar el punto de interrupción, se envía un [IDebugBreakpointErrorEvent2;](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) de lo `IDebugBreakpointBoundEvent2` contrario, se envía un.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)
