---
title: IDebugPropertyDestroyEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyDestroyEvent2
helpviewer_keywords:
- IDebugPropertyDestroyEvent2 interface
ms.assetid: 301b7a75-ecfa-46f1-9131-66cf3e4be147
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a52e9a1a3723566dd7a2dbdfc3cfe1a4d41261ed
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322757"
---
# <a name="idebugpropertydestroyevent2"></a>IDebugPropertyDestroyEvent2
Esta interfaz se envía por el motor de depuración (DE) el Administrador de depuración de la sesión (SDM) cuando una propiedad que está asociada a un documento específico se va a destruir.

## <a name="syntax"></a>Sintaxis

```
IDebugPropertyDestroyEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 La DE implementa esta interfaz para notificar que una propiedad se ha destruido. El [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaz debe implementarse en el mismo objeto que esta interfaz. Usa el SDM [QueryInterface](/cpp/atl/queryinterface) para tener acceso a la `IDebugEvent2` interfaz. Esta interfaz se implementa si la DE ha creado previamente una propiedad asociada con una secuencia de comandos; destruir la propiedad, quita el script asociado desde el IDE.

## <a name="notes-for-callers"></a>Notas para los llamadores
 La DE crea y envía este objeto de evento a una propiedad se ha destruido el informe. El evento se envía mediante la [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) función de devolución de llamada suministrada por el SDM cuando está conectado al programa que se está depurando.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestra el método de `IDebugPropertyDestroyEvent2`.

|Método|Descripción|
|------------|-----------------|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertydestroyevent2-getdebugproperty.md)|Obtiene la propiedad que se va a destruir.|

## <a name="remarks"></a>Comentarios
 Vea los comentarios sobre [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md) para obtener más información sobre por qué se usan estos eventos.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)