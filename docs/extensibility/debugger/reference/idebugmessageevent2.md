---
title: IDebugMessageEvent2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2
helpviewer_keywords:
- IDebugMessageEvent2 interface
ms.assetid: a9ff3d00-e9ac-4cd6-bda9-584a4815aff8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 180162988cbb09f98b7fc2e8f33f6b5d0ed322ae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727361"
---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
El motor de depuración (DE) usa esta interfaz para enviar un mensaje a Visual Studio que requiere una respuesta del usuario.

## <a name="syntax"></a>Sintaxis

```
IDebugMessageEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 La DE implementa esta interfaz para enviar un mensaje a Visual Studio que requiere una respuesta del usuario. El [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaz debe implementarse en el mismo objeto que esta interfaz. El SDM utiliza [QueryInterface](/cpp/atl/queryinterface) para tener acceso a la `IDebugEvent2` interfaz.

 La implementación de esta interfaz debe comunicar la llamada de Visual Studio de [SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md) a la DE. Por ejemplo, esto se puede hacer con un mensaje publicado en el subproceso de control de mensajes de la DE, o el `IDebugMessageEvent2::SetResponse`objeto que implementa esta interfaz podría contener una referencia a la DE y volver a llamar a la DE con la respuesta pasada a .

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 La DE crea y envía este objeto de evento para mostrar un mensaje al usuario que requiere una respuesta. El evento se envía mediante la función de devolución de llamada [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) proporcionada por el SDM cuando se adjunta al programa que se está depurando.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente `IDebugMessageEvent2`se muestran los métodos de .

|Método|Descripción|
|------------|-----------------|
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|Obtiene el mensaje que se va a mostrar.|
|[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|Establece la respuesta, si existe, desde el cuadro de mensaje.|

## <a name="remarks"></a>Observaciones
 El DE utilizará esta interfaz si requiere una respuesta específica del usuario para un mensaje determinado. Por ejemplo, si el DE recibe un mensaje "Acceso denegado" después de un intento de adjuntar `IDebugMessageEvent2` de forma remota `MB_RETRYCANCEL`a un programa, la DE envía este mensaje en particular a Visual Studio en un evento con el estilo de cuadro de mensaje . Esto permite al usuario reintentar o cancelar la operación de conexión.

 El DE especifica cómo se debe controlar este mensaje siguiendo las `MessageBox` convenciones de la función Win32 (consulte [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) para obtener más información).

 Use la [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) interfaz para enviar mensajes a Visual Studio que no requieren una respuesta del usuario.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
