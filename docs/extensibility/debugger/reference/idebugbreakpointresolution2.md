---
title: IDebugBreakpointResolution2 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBreakpointResolution2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 451d5bce-b9c1-48ff-beaa-2b4c3e1ceea0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f79ffdc3af15a9b18ca022e4234b4e6d97742387
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugbreakpointresolution2"></a>IDebugBreakpointResolution2
Esta interfaz representa la información que describe un punto de interrupción enlazado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugBreakpointResolution2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El motor de depuración (Alemania) implementa esta interfaz como parte de su compatibilidad con los puntos de interrupción. Esta interfaz proporciona una descripción de un punto de interrupción enlazado que utiliza el Administrador de depuración de sesión cuando el usuario ve propiedades de un punto de interrupción.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Una llamada a [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) devuelve esta interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugBreakpointResolution2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Obtiene el tipo del punto de interrupción representado por esta resolución.|  
|[GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Obtiene la información de resolución de punto de interrupción que describe este punto de interrupción.|  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)