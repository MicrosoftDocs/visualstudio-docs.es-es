---
title: "IDebugBreakpointRequest3 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBreakpointRequest3"
helpviewer_keywords: 
  - "IDebugBreakpointRequest3"
ms.assetid: 8a042beb-b319-48e3-b3c8-9c8336ab371b
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugBreakpointRequest3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz representa la información necesaria para crear y vincular a cualquier tipo de punto de interrupción.  es una extensión de [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md).  
  
## Sintaxis  
  
```  
IDebugBreakpointRequest3 : IDebugBreakpointRequest2  
```  
  
## Notas para los implementadores  
 El administrador de depuración de sesión \(SDM\) normalmente implementa esta interfaz.  
  
## Notas para los llamadores  
 El motor de depuración \(DE\) tiene acceso a esta interfaz llamando a [QueryInterface](/visual-cpp/atl/queryinterface) en la interfaz IDebugBreakpointRequest2 recibida en una llamada a [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md).  
  
## métodos en el orden de Vtable  
 Además de los métodos heredados de [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md), la interfaz `IDebugBreakpointRequest3` expone el método siguiente.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)|Obtiene la información de la solicitud de punto de interrupción que describe la solicitud de punto de interrupción.|  
  
## Comentarios  
 Esta interfaz se utiliza para proporcionar información adicional al OF a través de la estructura de [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) .  Esta información adicional incluye el identificador del proveedor de \(en forma de GUID\), el nombre de un punto, y el nombre de una restricción de punto de interrupción.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)   
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)