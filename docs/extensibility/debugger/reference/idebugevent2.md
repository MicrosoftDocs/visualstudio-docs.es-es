---
title: IDebugEvent2 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugEvent2
helpviewer_keywords:
- IDebugEvent2 interface
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
caps.latest.revision: 11
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
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: cf76a596a42b166a7e19686ecbae5fe4ddd41ea4
ms.lasthandoff: 04/05/2017

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
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
