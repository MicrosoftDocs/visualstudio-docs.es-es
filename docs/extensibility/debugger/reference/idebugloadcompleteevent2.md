---
title: IDebugLoadCompleteEvent2 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugLoadCompleteEvent2
helpviewer_keywords: IDebugLoadCompleteEvent2
ms.assetid: 37eb7360-28e9-4273-862a-4c17f22af690
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9ef666b3f7bbcaf75305cec10954df3355304515
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugloadcompleteevent2"></a>IDebugLoadCompleteEvent2
Esta interfaz se envía por el motor de depuración (Alemania) para el Administrador de sesión de depuración (SDM) cuando se carga un programa, pero antes de ejecutar cualquier código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugLoadCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 La DE implementa esta interfaz para notificar que se ha cargado correctamente un programa. El [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) debe implementar la interfaz en el mismo objeto que esta interfaz. Usa el SDM [QueryInterface](/cpp/atl/queryinterface) para tener acceso a la `IDebugEvent2` interfaz.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 El DIS crean y envía este objeto de evento para informar de que un programa se ha cargado correctamente. El evento se envía mediante la [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) función de devolución de llamada proporcionada por el SDM cuando adjunta al programa que se está depurando.  
  
## <a name="remarks"></a>Comentarios  
 Este evento es un evento de detención y debe tener la `EVENT_STOPPING` marcador establecido en los atributos del evento.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)