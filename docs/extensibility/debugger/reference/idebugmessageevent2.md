---
title: IDebugMessageEvent2 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMessageEvent2
helpviewer_keywords:
- IDebugMessageEvent2 interface
ms.assetid: a9ff3d00-e9ac-4cd6-bda9-584a4815aff8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6d0cb1f270d3d3ae77c43ea89fba5b7483e80412
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31116180"
---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
Esta interfaz se utiliza el motor de depuración (Alemania) para enviar un mensaje a Visual Studio que requiere una respuesta del usuario.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugMessageEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 La DE implementa esta interfaz para enviar un mensaje a Visual Studio que requiere una respuesta del usuario. El [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) debe implementar la interfaz en el mismo objeto que esta interfaz. Usa el SDM [QueryInterface](/cpp/atl/queryinterface) para tener acceso a la `IDebugEvent2` interfaz.  
  
 La implementación de esta interfaz debe comunicar llamada de Visual Studio de [SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md) a la DE. Por ejemplo, esto puede hacerse con un mensaje que se publican en el subproceso de control de mensajes de Alemania, o el objeto que implementa esta interfaz podría contener una referencia a la DE y devolver la llamada a la DE con la respuesta que se haya pasado al `IDebugMessageEvent2::SetResponse`.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 El DIS crean y envía este objeto de evento para mostrar un mensaje al usuario que solicita una respuesta. El evento se envía mediante la [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) función de devolución de llamada proporcionada por el SDM cuando se adjunta al programa que se está depurando.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugMessageEvent2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|Obtiene el mensaje que se mostrará.|  
|[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|Establece la respuesta, si existe, en el cuadro de mensaje.|  
  
## <a name="remarks"></a>Comentarios  
 La DE usará esta interfaz si requiere una respuesta específica del usuario para un mensaje determinado. Por ejemplo, si la DE recibe un mensaje de "Acceso denegado" después de un intento para asociar de forma remota a un programa, la DE envía este mensaje determinado a Visual Studio en un `IDebugMessageEvent2` eventos con el estilo de cuadro de mensaje `MB_RETRYCANCEL`. Esto permite al usuario volver a intentar o cancelar la operación de adjuntar.  
  
 La DE especifica cómo se administrará según las directrices de la función de Win32 este mensaje `MessageBox` (consulte [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) para obtener más información).  
  
 Use la [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) interfaz para enviar mensajes a Visual Studio que no requieren una respuesta del usuario.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)