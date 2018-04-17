---
title: IDebugBreakpointRequest3 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBreakpointRequest3
helpviewer_keywords:
- IDebugBreakpointRequest3
ms.assetid: 8a042beb-b319-48e3-b3c8-9c8336ab371b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f369b193b69ef1a08c2ad3d451ff989caae8939f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugbreakpointrequest3"></a>IDebugBreakpointRequest3
Esta interfaz representa la información necesaria para crear y enlazar cualquier tipo de punto de interrupción. Es una extensión de [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugBreakpointRequest3 : IDebugBreakpointRequest2  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Normalmente, el Administrador de sesión de depuración (SDM) implementa esta interfaz.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 El motor de depuración (Alemania) tiene acceso a esta interfaz mediante una llamada a [QueryInterface](/cpp/atl/queryinterface) en la interfaz de IDebugBreakpointRequest2 recibida en una llamada a [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md).  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 Además de los métodos heredados de [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md), el `IDebugBreakpointRequest3` interfaz expone el método siguiente.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)|Obtiene la información de solicitud de punto de interrupción que describe esta solicitud de punto de interrupción.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz se utiliza para proporcionar información adicional a la DE a través de la [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) estructura. Esta información adicional incluye el Id. del proveedor de Alemania (en forma de un GUID), el nombre de un punto de seguimiento y el nombre de una restricción de punto de interrupción.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)