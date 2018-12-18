---
title: IDebugEvent2 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEvent2
helpviewer_keywords:
- IDebugEvent2 interface
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: aff8be869bd65def16ca0519f7c87ea82320bb99
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31111216"
---
# <a name="idebugevent2"></a>IDebugEvent2
Esta interfaz se utiliza para comunicar información de depuración críticos, como detener en un punto de interrupción e información no críticos, como un mensaje de depuración.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El motor de depuración (Alemania) y el proveedor de puerto personalizado implementan esta interfaz en el mismo objeto que todas las demás interfaces de eventos.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Mediante la interfaz de argumento de identificador (IID) dado a [eventos](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) o [eventos](../../../extensibility/debugger/reference/idebugportevents2-event.md), el Administrador de sesión de depuración (SDM) llama [QueryInterface](/cpp/atl/queryinterface) en el `IDebugEvent2` interfaz para obtener la interfaz de eventos apropiado.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugEvent2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|Obtiene los atributos para este evento de depuración.|  
  
## <a name="remarks"></a>Comentarios  
 Interfaces de los eventos más específicos, como [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md), no se derivan de la interfaz IDebugEvent2, pero en su lugar, se implementa como una interfaz independiente en el mismo objeto como `IDebugEvent2`.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)