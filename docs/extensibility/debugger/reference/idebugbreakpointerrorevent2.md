---
title: IDebugBreakpointErrorEvent2 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBreakpointErrorEvent2
helpviewer_keywords:
- IDebugBreakpointErrorEvent2
ms.assetid: adee79df-8db5-4510-a7df-c50f4dbf5e35
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6f7cd8bdb5e8a36539807970958efda8f152e5c1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugbreakpointerrorevent2"></a>IDebugBreakpointErrorEvent2
Esta interfaz indica que el Administrador de sesión de depuración (SDM) que un punto de interrupción pendiente no se pudo enlazar a un programa cargado, ya sea debido a una advertencia o un error.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugBreakpointErrorEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 La DE implementa esta interfaz como parte de su compatibilidad con los puntos de interrupción. El [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) debe implementar la interfaz en el mismo objeto que esta interfaz (usa el SDM [QueryInterface](/cpp/atl/queryinterface) para tener acceso a la `IDebugEvent2` interfaz).  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 El DIS crean y envía este objeto de evento cuando no se puede enlazar a un punto de interrupción pendiente al programa que se está depurando. El evento se envía mediante la [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) función de devolución de llamada proporcionada por el SDM cuando adjunta al programa que se está depurando.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugBreakpointErrorEvent2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)|Obtiene el [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) interfaz que describe la advertencia o error.|  
  
## <a name="remarks"></a>Comentarios  
 Cada vez que se enlaza a un punto de interrupción, se envía un evento para el SDM. Si no se puede enlazar el punto de interrupción, un `IDebugBreakpointErrorEvent2` se envían; de lo contrario, un [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) se envía.  
  
 Por ejemplo, cuando no se puede analizar o evaluar la condición asociada con el punto de interrupción pendiente, se envía una advertencia que no se puede enlazar el punto de interrupción pendiente en este momento. Esto puede ocurrir si el código para el punto de interrupción no ha cargado todavía.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)