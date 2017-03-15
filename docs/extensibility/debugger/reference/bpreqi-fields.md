---
title: "BPREQI_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BPREQI_FIELDS"
helpviewer_keywords: 
  - "Enumeración BPREQI_FIELDS"
ms.assetid: 679e771e-4a79-484e-af37-f962ef4aa245
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# BPREQI_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Especifica la información que se recupere sobre una solicitud de punto de interrupción.  
  
## Sintaxis  
  
```cpp  
enum enum_BPREQI_FIELDS {   
   BPREQI_BPLOCATION   = 0x0001,  
   BPREQI_LANGUAGE     = 0x0002,  
   BPREQI_PROGRAM      = 0x0004,  
   BPREQI_PROGRAMNAME  = 0x0008,  
   BPREQI_THREAD       = 0x0010,  
   BPREQI_THREADNAME   = 0x0020,  
   BPREQI_PASSCOUNT    = 0x0040,  
   BPREQI_CONDITION    = 0x0080,  
   BPREQI_FLAGS        = 0x0100,  
   BPREQI_ALLOLDFIELDS = 0x01ff  
   BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only  
   BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only  
   BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only  
   BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only  
};  
typedef DWORD BPREQI_FIELDS;  
```  
  
```c#  
public enum enum_BPREQI_FIELDS {   
   BPREQI_BPLOCATION   = 0x0001,  
   BPREQI_LANGUAGE     = 0x0002,  
   BPREQI_PROGRAM      = 0x0004,  
   BPREQI_PROGRAMNAME  = 0x0008,  
   BPREQI_THREAD       = 0x0010,  
   BPREQI_THREADNAME   = 0x0020,  
   BPREQI_PASSCOUNT    = 0x0040,  
   BPREQI_CONDITION    = 0x0080,  
   BPREQI_FLAGS        = 0x0100,  
   BPREQI_ALLOLDFIELDS = 0x01ff  
   BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only  
   BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only  
   BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only  
   BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only  
};  
```  
  
## Members  
 BPREQI\_BPLOCATION  
 Inicializa y usan el campo de `bpLocation` \(ubicación de punto de interrupción\) de la estructura de [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) o de [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) .  
  
 BPREQI\_LANGUAGE  
 Inicializa y usan el campo de `guidLanguage` de la estructura de `BP_REQUEST_INFO` o de `BP_REQUEST_INFO2` .  
  
 BPREQI\_PROGRAM  
 Inicializa y usan el campo de `pProgram` de la estructura de `BP_REQUEST_INFO` o de `BP_REQUEST_INFO2` .  
  
 BPREQI\_PROGRAMNAME  
 Inicializa y usan el campo de `bstrProgramName` de la estructura de `BP_REQUEST_INFO` o de `BP_REQUEST_INFO2` .  
  
 BPREQI\_THREAD  
 Inicializa y usan el campo de `pThread` de la estructura de `BP_REQUEST_INFO` o de `BP_REQUEST_INFO2` .  
  
 BPREQI\_THREADNAME  
 Inicializa y usan el campo de `bstrThreadName` de la estructura de `BP_REQUEST_INFO` o de `BP_REQUEST_INFO2` .  
  
 BPREQI\_PASSCOUNT  
 Inicializa y usan el campo de `bpPassCount` de la estructura de `BP_REQUEST_INFO` o de `BP_REQUEST_INFO2` .  
  
 BPREQI\_CONDITION  
 Inicializa y usan el campo de `bpCondition` \(condición de punto de interrupción\) de la estructura de `BP_REQUEST_INFO` o de `BP_REQUEST_INFO2` .  
  
 BPREQI\_FLAGS  
 Inicializa y usan el campo de `dwFlags` de la estructura de `BP_REQUEST_INFO` o de `BP_REQUEST_INFO2` .  
  
 BPREQI\_ALLOLDFIELDS  
 Inicializa y el uso todos los campos de la estructura de `BP_REQUEST_INFO` .  
  
 BPREQI\_VENDOR  
 Inicializa y usan el campo de `guidVendor` de la estructura de `BP_REQUEST_INFO2` .  
  
 BPREQI\_CONSTRAINT  
 Inicializa y usan el campo de `bstrConstraint` de la estructura de `BP_REQUEST_INFO2` .  
  
 BPREQI\_TRACEPOINT  
 Inicializa y usan el campo de `bstrTracepoint` de la estructura de `BP_REQUEST_INFO2` .  
  
 BPREQI\_ALLFIELDS  
 Especifica todos los campos de la estructura de `BP_REQUEST_INFO2` .  
  
## Comentarios  
 Pasado como argumento a los métodos de [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) y de [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) para especificar los campos de las estructuras de [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) y de [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) se deben inicializar.  
  
 Estos marcadores también se utilizan para indicar qué campos de estructuras de `BP_REQUEST_INFO` y de `BP_REQUEST_INFO2` son utilizados y válidos cuando se devuelve cada estructura.  
  
 estos valores se pueden combinar con `OR`bit a bit.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)   
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)