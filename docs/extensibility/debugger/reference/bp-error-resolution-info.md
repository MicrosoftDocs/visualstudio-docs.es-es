---
title: "BP_ERROR_RESOLUTION_INFO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_ERROR_RESOLUTION_INFO"
helpviewer_keywords: 
  - "Estructura BP_ERROR_RESOLUTION_INFO"
ms.assetid: a6b83242-5728-4716-80f3-840c96d59c6c
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# BP_ERROR_RESOLUTION_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Describe la resolución de un punto de interrupción del error, incluyendo la ubicación, el programa, y subproceso.  
  
## Sintaxis  
  
```cpp#  
typedef struct _BP_ERROR_RESOLUTION_INFO {   
   BPERESI_FIELDS         dwFields;  
   BP_RESOLUTION_LOCATION bpResLocation;  
   IDebugProgram2*        pProgram;  
   IDebugThread2*         pThread;  
   BSTR                   bstrMessage;  
   BP_ERROR_TYPE          dwType;  
} BP_ERROR_RESOLUTION_INFO;  
```  
  
```c#  
public struct BP_ERROR_RESOLUTION_INFO {   
   public uint                   dwFields;  
   public BP_RESOLUTION_LOCATION bpResLocation;  
   public IDebugProgram2         pProgram;  
   public IDebugThread2          pThread;  
   public string                 bstrMessage;  
   public uint                   dwType;  
};  
```  
  
## Members  
 `dwFields`  
 Una combinación de valores de especificar la enumeración de [BPERESI\_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md) qué campos de esta estructura se completan.  
  
 `bpResLocation`  
 La combinación de [BP\_RESOLUTION\_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) , que especifica la ubicación de la resolución de punto de interrupción.  
  
 `pProgram`  
 El objeto de [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) que representa la aplicación en la que el error de punto de interrupción.  
  
 `pThread`  
 El objeto de [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) que representa el subproceso en el que la aplicación que generó el error de punto de interrupción está ejecutando.  
  
 `bstrMessage`  
 Una cadena que contiene cualquier advertencia o mensaje de error resultando de esta resolución del error.  
  
 `dwType`  
 Un valor de enumeración de [BP\_ERROR\_TYPE](../../../extensibility/debugger/reference/bp-error-type.md) que especifica el tipo de error de punto de interrupción.  
  
## Comentarios  
 Esta estructura se devuelve del método de [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) .  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)   
 [BPRESI\_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)   
 [BP\_RESOLUTION\_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP\_ERROR\_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)