---
title: IDebugBreakpointRequest3 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest3
helpviewer_keywords:
- IDebugBreakpointRequest3
ms.assetid: 8a042beb-b319-48e3-b3c8-9c8336ab371b
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 676251db2116e6d9101a0dcb6815f17a4e225192
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58996894"
---
# <a name="idebugbreakpointrequest3"></a>IDebugBreakpointRequest3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Esta interfaz representa la información necesaria para crear y enlazar cualquier tipo de punto de interrupción. Es una extensión de [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugBreakpointRequest3 : IDebugBreakpointRequest2  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El Administrador de depuración de la sesión (SDM) normalmente implementa esta interfaz.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 El motor de depuración (DE) tiene acceso a esta interfaz mediante una llamada a [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) en la interfaz IDebugBreakpointRequest2 recibida en una llamada a [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md).  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 Además de los métodos heredados de [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md), el `IDebugBreakpointRequest3` interfaz expone el método siguiente.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)|Obtiene la información de solicitud de punto de interrupción que describe esta solicitud de punto de interrupción.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz se usa para proporcionar información adicional a la DE a través de la [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) estructura. Esta información adicional incluye el Id. de proveedor de la DE (en forma de un GUID), el nombre de un punto de seguimiento y el nombre de una restricción de punto de interrupción.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
