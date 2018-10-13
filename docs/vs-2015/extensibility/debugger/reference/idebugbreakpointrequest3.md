---
title: IDebugBreakpointRequest3 | Documentos de Microsoft
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
- IDebugBreakpointRequest3
helpviewer_keywords:
- IDebugBreakpointRequest3
ms.assetid: 8a042beb-b319-48e3-b3c8-9c8336ab371b
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c7e5c09a407286b9825a3a58974010241be93608
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49265046"
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
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)

