---
title: IEnumDebugBoundBreakpoints2 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugBoundBreakpoints2
helpviewer_keywords:
- IEnumDebugBoundBreakpoints2
ms.assetid: ea03e7e1-28d6-40b7-8097-bbb61d3b7caa
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f5faeb96f32170fefa1f93a69ca08228ceaec11f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugboundbreakpoints2"></a>IEnumDebugBoundBreakpoints2
Esta interfaz enumera los puntos de interrupción enlazados asociados a un punto de interrupción pendiente o el punto de interrupción enlazado el evento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IEnumDebugBoundBreakpoints2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El motor de depuración (Alemania) implementa esta interfaz como parte de su compatibilidad con los puntos de interrupción. Si se admiten los puntos de interrupción, se debe implementar esta interfaz.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Visual Studio llama:  
  
-   [EnumBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) para obtener esta interfaz que representa una lista de todos los puntos de interrupción que se han activado.  
  
-   [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) para obtener esta interfaz que representa una lista de todos los puntos de interrupción que se enlazaron.  
  
-   [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) para obtener esta interfaz que representa una lista de todos los puntos de interrupción enlazado a ese punto de interrupción pendiente.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IEnumDebugBoundBreakpoints2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Siguiente](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)|Recupera un número especificado de los puntos de interrupción enlazados en una secuencia de enumeración.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-skip.md)|Omite un número especificado de puntos de interrupción enlazado en una secuencia de enumeración.|  
|[Restablecer](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-reset.md)|Restablece una secuencia de enumeración al principio.|  
|[clon](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-clone.md)|Crea un enumerador que contiene el mismo estado de enumeración que el enumerador actual.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-getcount.md)|Obtiene el número de puntos de interrupción enlazados en un enumerador.|  
  
## <a name="remarks"></a>Comentarios  
 Visual Studio utiliza los puntos de interrupción enlazados representados por esta interfaz para actualizar la pantalla de puntos de interrupción en el IDE.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)