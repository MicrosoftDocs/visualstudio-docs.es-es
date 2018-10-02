---
title: IDebugEvent2 | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEvent2
helpviewer_keywords:
- IDebugEvent2 interface
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7fc387733e1472afe5f21f5e0638374ebda9f677
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47582989"
---
# <a name="idebugevent2"></a>IDebugEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IDebugEvent2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugevent2).  
  
Esta interfaz se utiliza para comunicar información de depuración importante, como detener en un punto de interrupción y la información no críticos, como un mensaje de depuración.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El motor de depuración (DE) y el proveedor de puerto personalizado debe implementar esta interfaz en el mismo objeto que todas las demás interfaces de eventos.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Mediante la interfaz de argumento de identificador (IID) dado a [eventos](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) o [eventos](../../../extensibility/debugger/reference/idebugportevents2-event.md), el Administrador de depuración de la sesión (SDM) llama a [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) en el `IDebugEvent2` interfaz para obtener la interfaz de eventos adecuado.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugEvent2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|Obtiene los atributos de este evento de depuración.|  
  
## <a name="remarks"></a>Comentarios  
 El evento más específico las interfaces, como [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md), no se derivan de la interfaz IDebugEvent2, pero en su lugar se implementan como una interfaz independiente en el mismo objeto que `IDebugEvent2`.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces del núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)

