---
title: IDebugProcessDestroyEvent2 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcessDestroyEvent2
helpviewer_keywords: IDebugProcessDestroyEvent2
ms.assetid: 1b8e0528-95bc-48fa-9653-2cea66c8dc3a
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 91eb4e9f749111e96bec2e527432b1f1851cd24c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprocessdestroyevent2"></a>IDebugProcessDestroyEvent2
Esta interfaz se envía cuando un proceso se termina, atípicamente se cierra o se separa de.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugProcessDestroyEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El motor de depuración (Alemania) o el proveedor del puerto personalizado implementan esta interfaz para notificar que un proceso ha finalizado. El [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) debe implementar la interfaz en el mismo objeto que esta interfaz. Usa el SDM [QueryInterface](/cpp/atl/queryinterface) para tener acceso a la `IDebugEvent2` interfaz.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 El proveedor de puerto personalizado o la DE crea y envía este objeto de evento para notificar la finalización de un proceso. La DE envía este evento mediante el [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) función de devolución de llamada proporcionada por el SDM cuando se adjunta al programa que se está depurando. El proveedor de puerto personalizado envía este evento mediante el [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) interfaz.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)