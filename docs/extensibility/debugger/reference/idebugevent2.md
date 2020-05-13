---
title: IDebugEvent2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEvent2
helpviewer_keywords:
- IDebugEvent2 interface
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6341f8003b962a7f45420b076b23623ebdaf861
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729913"
---
# <a name="idebugevent2"></a>IDebugEvent2
Esta interfaz se utiliza para comunicar información de depuración crítica, como la detención en un punto de interrupción, y la información no crítica, como un mensaje de depuración.

## <a name="syntax"></a>Sintaxis

```
IDebugEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El motor de depuración (DE) y el proveedor de puertos personalizado implementan esta interfaz en el mismo objeto que todas las demás interfaces de eventos.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 Mediante el argumento ID de interfaz (IID) dado a [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) o [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md) `IDebugEvent2` , el administrador de depuración de sesión (SDM) llama a [QueryInterface](/cpp/atl/queryinterface) en la interfaz para obtener la interfaz de eventos adecuada.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente `IDebugEvent2`se muestran los métodos de .

|Método|Descripción|
|------------|-----------------|
|[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|Obtiene los atributos de este evento de depuración.|

## <a name="remarks"></a>Observaciones
 Las interfaces de eventos más específicas, como [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md), no derivan de la interfaz IDebugEvent2, sino que se implementan como una interfaz independiente en el mismo objeto que `IDebugEvent2`.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
