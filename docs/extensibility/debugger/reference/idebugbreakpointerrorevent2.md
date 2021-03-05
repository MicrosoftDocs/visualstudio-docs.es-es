---
description: Esta interfaz indica al administrador de depuración de la sesión (SDM) que un punto de interrupción pendiente no se pudo enlazar a un programa cargado, ya sea debido a una advertencia o un error.
title: IDebugBreakpointErrorEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointErrorEvent2
helpviewer_keywords:
- IDebugBreakpointErrorEvent2
ms.assetid: adee79df-8db5-4510-a7df-c50f4dbf5e35
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 89342f5d26c5aeec41222bba12a29f534798782b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143367"
---
# <a name="idebugbreakpointerrorevent2"></a>IDebugBreakpointErrorEvent2
Esta interfaz indica al administrador de depuración de la sesión (SDM) que un punto de interrupción pendiente no se pudo enlazar a un programa cargado, ya sea debido a una advertencia o un error.

## <a name="syntax"></a>Syntax

```
IDebugBreakpointErrorEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El DE implementa esta interfaz como parte de su compatibilidad con los puntos de interrupción. La interfaz [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) debe implementarse en el mismo objeto que esta interfaz (el SDM usa [QueryInterface](/cpp/atl/queryinterface) para tener acceso a la `IDebugEvent2` interfaz).

## <a name="notes-for-callers"></a>Notas para llamadores
 Crea y envía este objeto DE evento cuando no se puede enlazar un punto de interrupción pendiente al programa que se está depurando. El evento se envía mediante la función de devolución de llamada [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) proporcionada por el SDM cuando se adjunta al programa que se está depurando.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IDebugBreakpointErrorEvent2` .

|Método|Descripción|
|------------|-----------------|
|[GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)|Obtiene la interfaz [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) que describe la advertencia o el error.|

## <a name="remarks"></a>Observaciones
 Siempre que se enlaza un punto de interrupción, se envía un evento al SDM. Si no se puede enlazar el punto de interrupción, `IDebugBreakpointErrorEvent2` se envía un; en caso contrario, se envía un [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) .

 Por ejemplo, cuando la condición asociada al punto de interrupción pendiente no se puede analizar o evaluar, se envía una advertencia que indica que no se puede enlazar el punto de interrupción pendiente en este momento. Esto puede ocurrir si aún no se ha cargado el código del punto de interrupción.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
