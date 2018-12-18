---
title: IDebugCanStopEvent2 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCanStopEvent2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 48f049648fcbd93d7ad7411a4dfeba8bbdb4431d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31105611"
---
# <a name="idebugcanstopevent2"></a>IDebugCanStopEvent2
Esta interfaz se usa para solicitar al administrador de sesión de depuración (SDM) si se detiene en la ubicación actual del código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugCanStopEvent2 : IUknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El motor de depuración (Alemania) implementa esta interfaz para admitir la ejecución paso a paso por el código fuente. El [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) debe implementar la interfaz en el mismo objeto que esta interfaz (usa el SDM [QueryInterface](/cpp/atl/queryinterface) para tener acceso a la `IDebugEvent2` interfaz).  
  
 La implementación de esta interfaz debe comunicar llamada de SDM de [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) para el motor de depuración. Por ejemplo, esto puede hacerse con un mensaje que se publican en el subproceso de control de mensajes del motor de depuración o podría mantener una referencia al motor de depuración y se devuelva la llamada al motor de depuración con el indicador que se pasan en el objeto que implementa esta interfaz `IDebugCanStopEvent2::CanStop`.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Puede enviar la DE este método cada vez que se solicita el Alemania para continuar la ejecución y la DE está recorriendo el código. Este evento se envía mediante la [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) función de devolución de llamada proporcionada por el SDM cuando adjunta al programa que se está depurando.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugCanStopEvent2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)|Obtiene el motivo de este evento.|  
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|Especifica si el programa que se está depurando debe detenerse en la ubicación de este evento (y enviar un evento que describe la razón de detención) o simplemente continuar la ejecución.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|Obtiene el contexto del documento que describe la ubicación de este evento.|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|Obtiene el contexto del código que describe la ubicación de este evento.|  
  
## <a name="remarks"></a>Comentarios  
 La DE envía esta interfaz si no encuentra que los pasos de usuario en una función y la DE ninguna información de depuración no existe o existe información de depuración pero la DE no sabe si el código fuente se puede mostrar para esa ubicación.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)