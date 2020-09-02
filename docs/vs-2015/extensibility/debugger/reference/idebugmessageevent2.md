---
title: IDebugMessageEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2
helpviewer_keywords:
- IDebugMessageEvent2 interface
ms.assetid: a9ff3d00-e9ac-4cd6-bda9-584a4815aff8
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e7bb6b014ef8aa662abd42ab2989d47f703880a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685970"
---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

El motor DE depuración (DE) usa esta interfaz para enviar un mensaje a Visual Studio que requiere una respuesta del usuario.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugMessageEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El DE implementa esta interfaz para enviar un mensaje a Visual Studio que requiere una respuesta del usuario. La interfaz [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) debe implementarse en el mismo objeto que esta interfaz. El SDM usa [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) para tener acceso a la `IDebugEvent2` interfaz.  
  
 La implementación de esta interfaz debe comunicar la llamada de Visual Studio de [SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md) al de. Por ejemplo, esto se puede hacer con un mensaje expuesto al subproceso DE CONTROL DE mensajes DE, o el objeto que implementa esta interfaz podría contener una referencia a la DE y volver a llamar a la DE con la respuesta que se pasa a `IDebugMessageEvent2::SetResponse` .  
  
## <a name="notes-for-callers"></a>Notas para llamadores  
 El DE crea y envía este objeto de evento para mostrar un mensaje al usuario que requiere una respuesta. El evento se envía mediante la función de devolución de llamada [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) proporcionada por el SDM cuando se adjunta al programa que se está depurando.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 En la tabla siguiente se muestran los métodos de `IDebugMessageEvent2` .  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|Obtiene el mensaje que se va a mostrar.|  
|[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|Establece la respuesta, si existe, en el cuadro de mensaje.|  
  
## <a name="remarks"></a>Observaciones  
 El DE utilizará esta interfaz si requiere una respuesta específica del usuario para un mensaje determinado. Por ejemplo, si el DE obtiene un mensaje "acceso denegado" después de un intento de adjuntar de forma remota a un programa, el DE envía este mensaje determinado a Visual Studio en un `IDebugMessageEvent2` evento con el estilo de cuadro de mensaje `MB_RETRYCANCEL` . Esto permite al usuario Reintentar o cancelar la operación de adjuntar.  
  
 El DE especifica cómo debe controlarse este mensaje siguiendo las convenciones de la función de Win32 `MessageBox` (vea [AfxMessageBox](https://msdn.microsoft.com/library/d66d0328-cdcc-48f6-96a4-badf089099c8) para obtener más información).  
  
 Use la interfaz [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) para enviar mensajes a Visual Studio que no requieran una respuesta del usuario.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg. h  
  
 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte también  
 [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
