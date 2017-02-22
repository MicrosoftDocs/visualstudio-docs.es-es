---
title: "BP_REQUEST_INFO | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_REQUEST_INFO"
helpviewer_keywords: 
  - "Estructura BP_REQUEST_INFO"
ms.assetid: 42a31412-5b6b-47fe-a762-0c2bc769e1cc
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# BP_REQUEST_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Contiene la información necesaria para implementar un punto de interrupción.  
  
## Sintaxis  
  
```cpp#  
typedef struct _BP_REQUEST_INFO {  
   BPREQI_FIELDS   dwFields;  
   GUID            guidLanguage;  
   BP_LOCATION     bpLocation;  
   IDebugProgram2* pProgram;  
   BSTR            bstrProgramName;  
   IDebugThread2*  pThread;  
   BSTR            bstrThreadName;  
   BP_CONDITION    bpCondition;  
   BP_PASSCOUNT    bpPassCount;  
   BP_FLAGS        dwFlags;  
} BP_REQUEST_INFO;  
```  
  
```c#  
public struct BP_REQUEST_INFO {  
   public uint           dwFields;  
   public Guid           guidLanguage;  
   public BP_LOCATION    bpLocation;  
   public IDebugProgram2 pProgram;  
   public string         bstrProgramName;  
   public IDebugThread2  pThread;  
   public string         bstrThreadName;  
   public BP_CONDITION   bpCondition;  
   public BP_PASSCOUNT   bpPassCount;  
   public uint           dwFlags;  
};  
```  
  
## Members  
 `dwFields`  
 Una combinación de marcadores de enumeración de [BPREQI\_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) que especifica se completan los campos.  
  
 `guidLanguage`  
 el lenguaje GUID.  
  
 `bpLocation`  
 La estructura de [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md) que especifica el tipo de ubicación de punto de interrupción.  
  
 `pProgram`  
 El objeto de [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) que representa la aplicación en la que el punto de interrupción.  
  
 `bstrProgramName`  
 El nombre de la aplicación en la que el punto de interrupción.  
  
 `pThread`  
 El objeto de [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) que representa el subproceso en el que el punto de interrupción.  
  
 `bstrThreadName`  
 El nombre del subproceso en el que el punto de interrupción.  
  
 `bpCondition`  
 La estructura de [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) que describe las condiciones en las que el punto de interrupción desencadenará.  
  
 `bpPassCount`  
 La estructura de [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) que contiene la información del recuento del paso de punto de interrupción.  
  
 `dwFlags`  
 Una combinación de marcadores de enumeración de [BP\_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) que especifica los marcadores para el punto de interrupción solicitado.  
  
## Comentarios  
 esta estructura es devuelta por el método de [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) .  
  
 Si necesita obtener el GUID del proveedor del motor de depuración, la restricción del punto de interrupción o punto de seguimiento, vea la estructura de [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) .  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)   
 [BPREQI\_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)   
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)   
 [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP\_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)   
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)