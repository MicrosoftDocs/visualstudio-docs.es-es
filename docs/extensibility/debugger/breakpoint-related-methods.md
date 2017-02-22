---
title: "M&#233;todos relacionados con el punto de interrupci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "depurar [SDK de depuración], métodos de punto de interrupción"
  - "puntos de interrupción, métodos"
ms.assetid: a6f77bf0-bf81-443f-8683-5f12075bbe10
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# M&#233;todos relacionados con el punto de interrupci&#243;n
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un motor de depuración \(DE\) debe admitir el valor de puntos de interrupción.  Depuración de Visual Studio admite los siguientes tipos de puntos de interrupción:  
  
-   De enlace  
  
     Solicitado con la interfaz de usuario y enlazado correctamente en una ubicación especificada del código  
  
-   pendiente  
  
     Solicitado con la interfaz de usuario pero todavía no enlazado a las instrucciones reales  
  
## Explicación  
 Por ejemplo, un punto de interrupción pendiente aparece cuando las instrucciones no se cargan.  Cuando se carga el código, hasta que finalice el intento de puntos de interrupción a vincular al código en la ubicación prescrita, es decir, las instrucciones de la interrupción de inserción en el código.  Los eventos se envían al administrador \(SDM\) de depuración de la sesión para indicar el enlace correcto o para notificarlo que había errores de enlace.  
  
 Un punto de interrupción pendiente también administra su propia lista de corresponder los puntos de interrupción enlazados.  Uno hasta que finalice el punto de interrupción puede provocar la inserción de muchos puntos de interrupción en el código.  La interfaz de usuario de depuración de Visual Studio muestra una vista de árbol de puntos de interrupción pendientes y sus puntos de interrupción enlazados correspondientes.  
  
 La creación y el uso de puntos de interrupción pendientes requieren la implementación del método de [IDebugEngine2:: CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) así como de los métodos siguientes de interfaces de [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) .  
  
|Método|Descripción|  
|------------|-----------------|  
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Determina si especificado hasta que finalice el punto de interrupción puede enlazar a una ubicación del código.|  
|[Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Enlaza especificado hasta que finalice el punto de interrupción a una o varias ubicaciones del código.|  
|[GetState](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Obtiene el estado de un punto de interrupción pendiente.|  
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Obtiene la solicitud de punto de interrupción utilizada para crear un punto de interrupción pendiente.|  
|[Habilitar](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Alterna el estado habilitado de un punto de interrupción pendiente.|  
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Muestra todos los puntos de interrupción enlazados de un punto de interrupción pendiente.|  
|[EnumErrorBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Muestra todos los puntos de interrupción del error que son el resultado de un punto de interrupción pendiente.|  
|[Eliminar](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Elimina un punto de interrupción pendiente y todos los puntos de interrupción enlazados de.|  
  
 Para enumerar los puntos de interrupción enlazados y los puntos de interrupción del error, debe implementar todos los métodos de [IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) y de [IEnumDebugErrorBreakpoints2](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md).  
  
 Pendientes los puntos de interrupción que se enlazan a una ubicación de código requiere la implementación de los métodos siguientes de [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) .  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|obtiene el punto de interrupción pendiente que contiene un punto de interrupción.|  
|[GetState](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Obtiene el estado de un punto de interrupción enlazado.|  
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Obtiene la resolución de punto de interrupción que describe un punto de interrupción.|  
|[Habilitar](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Habilita o deshabilita un punto de interrupción.|  
|[Eliminar](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|elimina un punto de interrupción enlazado.|  
  
 La información de resolución y solicitar requiere la implementación de los métodos siguientes de [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) .  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Obtiene el tipo de punto de interrupción representado por una resolución.|  
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Obtiene la información de resolución de punto de interrupción que describe un punto de interrupción.|  
  
 La resolución de los errores que pueden producirse durante el enlace requiere la implementación de los métodos siguientes de [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) .  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|Obtiene el punto de interrupción pendiente que contiene un punto de interrupción del error.|  
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|Obtiene la resolución del error de punto de interrupción que describe un punto de interrupción del error.|  
  
 La resolución de los errores que pueden producirse durante enlazar también requiere los siguientes métodos de [IDebugErrorBreakpointResolution2](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md).  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|obtiene el tipo de un punto de interrupción.|  
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|obtiene la información de la resolución de un punto de interrupción.|  
  
 Ver el código fuente en un punto de interrupción requiere implementar los métodos de [IDebugStackFrame2:: GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) métodos y\/o de [IDebugStackFrame2:: GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md).  
  
## Vea también  
 [Control de ejecución y evaluación de estado](../../extensibility/debugger/execution-control-and-state-evaluation.md)