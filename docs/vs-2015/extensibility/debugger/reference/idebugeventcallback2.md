---
title: IDebugEventCallback2 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEventCallback2
helpviewer_keywords:
- IDebugEventCallback2
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2c1e0f6425b6c466d54b6ed24bace0e406e7035d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51792104"
---
# <a name="idebugeventcallback2"></a>IDebugEventCallback2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Esta interfaz se utiliza el motor de depuración (DE) para enviar eventos de depuración para el Administrador de depuración de la sesión (SDM).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugEventCallback2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] implementa esta interfaz para recibir eventos de un motor de depuración.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Un motor de depuración normalmente recibe esta interfaz cuando se llama el SDM [adjuntar](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [adjuntar](../../../extensibility/debugger/reference/idebugengine2-attach.md), o [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md). Un motor de depuración envía eventos al SDM mediante una llamada a [eventos](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugEventCallback2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|Envía una notificación de eventos para el SDM la depuración.|  
  
## <a name="remarks"></a>Comentarios  
 Aunque [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) y [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) especificar que llevan una `IDebugEventCallback2` interfaz, esto no es el caso, y el puntero de interfaz siempre será un valor null. En su lugar, debe usar el motor de depuración del `IDebugEventCallback2` interfaz recibidos en la llamada a [adjuntar](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [adjuntar](../../../extensibility/debugger/reference/idebugengine2-attach.md), o [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
 Si implementa un paquete [IDebugEventCallback](../../../extensibility/debugger/reference/idebugeventcallback2.md) en código administrado, es muy recomendable que <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> invocarse en las distintas interfaces que se pasan a [eventos](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces del núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Adjuntar](../../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [Asociar](../../../extensibility/debugger/reference/idebugengine2-attach.md)

