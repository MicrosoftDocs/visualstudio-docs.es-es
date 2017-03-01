---
title: IDebugMessageEvent2 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugMessageEvent2
helpviewer_keywords:
- IDebugMessageEvent2 interface
ms.assetid: a9ff3d00-e9ac-4cd6-bda9-584a4815aff8
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 0f033c5793dc3b89a1f2bd74a2bc4857730fb746
ms.lasthandoff: 02/22/2017

---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
Esta interfaz se utiliza el motor de depuración (DE) para enviar un mensaje a Visual Studio que requiere una respuesta del usuario.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugMessageEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 La DE implementa esta interfaz para enviar un mensaje a Visual Studio que requiere una respuesta del usuario. El [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaz se debe implementar en el mismo objeto que esta interfaz. Usa el SDM [QueryInterface](/visual-cpp/atl/queryinterface) para tener acceso a la `IDebugEvent2` interfaz.  
  
 La implementación de esta interfaz debe comunicar la llamada de Visual Studio de [SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md) a la DE. Por ejemplo, esto puede hacerse con un mensaje publicado al mensaje de la DE control de subproceso o el objeto que implementa esta interfaz podría contener una referencia a la DE y devolver la llamada a la DE con la respuesta pasada a `IDebugMessageEvent2::SetResponse`.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 El DE crea y envía este objeto de evento para mostrar un mensaje al usuario que requiere una respuesta. El evento se envía mediante la [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) función de devolución de llamada proporcionada por el SDM cuando está conectado al programa que se está depurando.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La siguiente tabla muestra los métodos de `IDebugMessageEvent2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|Obtiene el mensaje que se mostrará.|  
|[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|Establece la respuesta, si hay alguno, en el cuadro de mensaje.|  
  
## <a name="remarks"></a>Comentarios  
 La DE usará esta interfaz si se requiere una respuesta específica del usuario para un mensaje determinado. Por ejemplo, si la DE Obtiene un mensaje de "Acceso denegado" después de intentar conectar remotamente a un programa, la DE envía este mensaje determinado a Visual Studio en un `IDebugMessageEvent2` evento con el estilo de cuadro de mensaje `MB_RETRYCANCEL`. Esto permite al usuario volver a intentar o cancelar la operación de adjuntar.  
  
 La DE especifica cómo se administrará las directrices de la función de Win32 este mensaje `MessageBox` (consulte [AfxMessageBox](http://msdn.microsoft.com/Library/d66d0328-cdcc-48f6-96a4-badf089099c8) para obtener más información).  
  
 Utilice la [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) interfaz para enviar mensajes a Visual Studio que no requieren una respuesta del usuario.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
