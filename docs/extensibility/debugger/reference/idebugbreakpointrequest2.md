---
title: IDebugBreakpointRequest2 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBreakpointRequest2
helpviewer_keywords: IDebugBreakpointRequest2 interface
ms.assetid: 01ac4013-96f9-4235-b289-f55f9e99558f
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f458d8efcf1a4b466cc48dfd9dca10fa356a6304
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugbreakpointrequest2"></a>IDebugBreakpointRequest2
Esta interfaz representa la información necesaria para crear y enlazar cualquier tipo de punto de interrupción.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugBreakpointRequest2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Normalmente, el Administrador de sesión de depuración (SDM) implementa esta interfaz.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 El motor de depuración (Alemania) recibe esta interfaz mediante una llamada a [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) con el fin de crear un punto de interrupción pendiente. Una llamada a [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md) puede recuperar esta interfaz de la DE.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugBreakpointRequest2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)|Obtiene el tipo de ubicación de punto de interrupción de esta solicitud de punto de interrupción.|  
|[GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)|Obtiene la información de solicitud de punto de interrupción que describe esta solicitud de punto de interrupción.|  
  
## <a name="remarks"></a>Comentarios  
 Después el programa que se está depurando se han cargado, una llamada a [enlazar](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) enlaza un punto de interrupción pendiente a la ubicación solicitada en el programa.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)   
 [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)   
 [Enlazar](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)