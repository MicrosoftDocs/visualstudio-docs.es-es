---
title: IDebugEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEvent2
helpviewer_keywords:
- IDebugEvent2 interface
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e70767bab6453f3c3d96b58c8be049a832dc6ad
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62920193"
---
# <a name="idebugevent2"></a>IDebugEvent2
Esta interfaz se utiliza para comunicar información de depuración importante, como detener en un punto de interrupción y la información no críticos, como un mensaje de depuración.

## <a name="syntax"></a>Sintaxis

```
IDebugEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El motor de depuración (DE) y el proveedor de puerto personalizado debe implementar esta interfaz en el mismo objeto que todas las demás interfaces de eventos.

## <a name="notes-for-callers"></a>Notas para los llamadores
 Mediante la interfaz de argumento de identificador (IID) dado a [eventos](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) o [eventos](../../../extensibility/debugger/reference/idebugportevents2-event.md), el Administrador de depuración de la sesión (SDM) llama a [QueryInterface](/cpp/atl/queryinterface) en el `IDebugEvent2` interfaz para obtener la interfaz de eventos adecuado.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 La tabla siguiente muestran los métodos de `IDebugEvent2`.

|Método|Descripción|
|------------|-----------------|
|[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|Obtiene los atributos de este evento de depuración.|

## <a name="remarks"></a>Comentarios
 El evento más específico las interfaces, como [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md), no se derivan de la interfaz IDebugEvent2, pero en su lugar se implementan como una interfaz independiente en el mismo objeto que `IDebugEvent2`.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)