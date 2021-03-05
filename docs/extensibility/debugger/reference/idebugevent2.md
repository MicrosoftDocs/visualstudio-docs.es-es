---
description: Esta interfaz se usa para comunicar la información de depuración crítica, como la detención en un punto de interrupción, y la información no crítica, como un mensaje de depuración.
title: IDebugEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEvent2
helpviewer_keywords:
- IDebugEvent2 interface
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e162e276fc93c9e2c0d4333ac0f5c2630f75618e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152954"
---
# <a name="idebugevent2"></a>IDebugEvent2
Esta interfaz se usa para comunicar la información de depuración crítica, como la detención en un punto de interrupción, y la información no crítica, como un mensaje de depuración.

## <a name="syntax"></a>Syntax

```
IDebugEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El motor DE depuración (DE) y el proveedor del puerto personalizado implementan esta interfaz en el mismo objeto que todas las demás interfaces de eventos.

## <a name="notes-for-callers"></a>Notas para llamadores
 Con el argumento de ID. de interfaz (IID) dado al [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) o [evento](../../../extensibility/debugger/reference/idebugportevents2-event.md), el administrador de depuración de sesión (SDM) llama a [QueryInterface](/cpp/atl/queryinterface) en la `IDebugEvent2` interfaz para obtener la interfaz de eventos adecuada.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IDebugEvent2` .

|Método|Descripción|
|------------|-----------------|
|[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|Obtiene los atributos para este evento de depuración.|

## <a name="remarks"></a>Observaciones
 Las interfaces de eventos más específicas, como [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md), no se derivan de la interfaz IDebugEvent2, sino que se implementan como una interfaz independiente en el mismo objeto que `IDebugEvent2` .

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
