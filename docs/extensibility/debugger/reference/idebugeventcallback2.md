---
title: IDebugEventCallback2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEventCallback2
helpviewer_keywords:
- IDebugEventCallback2
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 68d29d928f310cb045ed712a151f9275446465a4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31116209"
---
# <a name="idebugeventcallback2"></a>IDebugEventCallback2
Esta interfaz se utiliza el motor de depuración (Alemania) para enviar eventos de depuración para el Administrador de sesión de depuración (SDM).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugEventCallback2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] implementa esta interfaz para recibir eventos de un motor de depuración.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Un motor de depuración normalmente recibe esta interfaz cuando se llama a la SDM [adjuntar](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [adjuntar](../../../extensibility/debugger/reference/idebugengine2-attach.md), o [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md). Un motor de depuración envía eventos a lo SDM mediante una llamada a [eventos](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugEventCallback2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|Envía una notificación de eventos para el SDM de depuración.|  
  
## <a name="remarks"></a>Comentarios  
 Aunque [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) y [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) especificar que toman un `IDebugEventCallback2` interfaz, este no es el caso y el puntero de interfaz siempre será un valor null. En su lugar, debe usar el motor de depuración del `IDebugEventCallback2` interfaz recibido en la llamada a [adjuntar](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [adjuntar](../../../extensibility/debugger/reference/idebugengine2-attach.md), o [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
 Si implementa un paquete [IDebugEventCallback](../../../extensibility/debugger/reference/idebugeventcallback2.md) en código administrado, es muy recomendable que <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> se puede invocar en las diversas interfaces que se pasan a [eventos](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Adjuntar](../../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [Asociar](../../../extensibility/debugger/reference/idebugengine2-attach.md)