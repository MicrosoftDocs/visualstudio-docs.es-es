---
title: IDebugPropertyCreateEvent2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyCreateEvent2
helpviewer_keywords:
- IDebugPropertyCreateEvent2 interface
ms.assetid: 33b3082b-a42e-488a-a1e4-dadf506f922c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84d8fcb4375f29820b51752ac3fdebbd04f06f80
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720930"
---
# <a name="idebugpropertycreateevent2"></a>IDebugPropertyCreateEvent2
Esta interfaz es enviada por el motor de depuración (DE) al administrador de depuración de sesión (SDM) cuando crea una propiedad que está asociada a un documento específico.

## <a name="syntax"></a>Sintaxis

```
IDebugPropertyCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 La DE implementa esta interfaz para informar de que se ha creado una propiedad. El [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaz debe implementarse en el mismo objeto que esta interfaz. El SDM utiliza [QueryInterface](/cpp/atl/queryinterface) para tener acceso a la `IDebugEvent2` interfaz. Esta interfaz se implementa si la DE ha creado una propiedad asociada a un script que se ha cargado o creado y si ese script debe aparecer en el IDE.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 El DE crea y envía este objeto de evento para informar de que se ha creado una propiedad. El evento se envía mediante la función de devolución de llamada [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) proporcionada por el SDM cuando se adjunta al programa que se está depurando.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente `IDebugPropertyCreateEvent2` se muestra el método de la interfaz.

|Método|Descripción|
|------------|-----------------|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)|Obtiene la nueva propiedad.|

## <a name="remarks"></a>Observaciones
 Si una propiedad tiene un documento o script específico asociado a él, el DE puede enviar este evento al SDM para actualizar la ventana de los **documentos** de script con el nombre del documento. El SDM llamará a [GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md) con el argumento `guidDocument` para recuperar un `VARIANT` contenedor de un [IUnknown](/cpp/atl/iunknown) puntero. El SDM llamará [queryInterface](/cpp/atl/queryinterface) en este puntero para recuperar el [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interfaz que se usa para actualizar el **documentos** de script ventana.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
