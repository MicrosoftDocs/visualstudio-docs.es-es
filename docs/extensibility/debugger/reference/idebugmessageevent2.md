---
title: IDebugMessageEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2
helpviewer_keywords:
- IDebugMessageEvent2 interface
ms.assetid: a9ff3d00-e9ac-4cd6-bda9-584a4815aff8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 49224ad0018286fffd365857364bf1b37300788f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62918836"
---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
Esta interfaz se utiliza el motor de depuración (DE) para enviar un mensaje a Visual Studio que requiere una respuesta del usuario.

## <a name="syntax"></a>Sintaxis

```
IDebugMessageEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 La DE implementa esta interfaz para enviar un mensaje a Visual Studio que requiere una respuesta del usuario. El [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaz debe implementarse en el mismo objeto que esta interfaz. Usa el SDM [QueryInterface](/cpp/atl/queryinterface) para tener acceso a la `IDebugEvent2` interfaz.

 La implementación de esta interfaz debe comunicar la llamada de Visual Studio de [SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md) a la DE. Por ejemplo, esto puede hacerse con un mensaje enviado al mensaje de la DE subproceso de control o el objeto que implementa esta interfaz podría contener una referencia a la DE y devolver la llamada a la DE la respuesta que se pasó `IDebugMessageEvent2::SetResponse`.

## <a name="notes-for-callers"></a>Notas para los llamadores
 La DE crea y envía este objeto de evento para mostrar un mensaje al usuario que solicita una respuesta. El evento se envía mediante la [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) función de devolución de llamada suministrada por el SDM cuando está conectado al programa que se está depurando.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 La tabla siguiente muestran los métodos de `IDebugMessageEvent2`.

|Método|Descripción|
|------------|-----------------|
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|Obtiene el mensaje que se mostrará.|
|[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|Establece la respuesta, si existe, en el cuadro de mensaje.|

## <a name="remarks"></a>Comentarios
 La DE usará esta interfaz si se requiere una respuesta específica del usuario para un mensaje determinado. Por ejemplo, si la DE Obtiene un mensaje de "Acceso denegado" después de un intento de forma remota, asociar a un programa, la DE envía este mensaje en concreto a Visual Studio en un `IDebugMessageEvent2` eventos con el estilo de cuadro de mensaje `MB_RETRYCANCEL`. Esto permite al usuario volver a intentar o cancelar la operación de adjuntar.

 La DE especifica cómo se administrará según las directrices de la función de Win32 este mensaje `MessageBox` (consulte [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) para obtener más información).

 Use la [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) interfaz para enviar mensajes a Visual Studio que no requieren una respuesta del usuario.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)