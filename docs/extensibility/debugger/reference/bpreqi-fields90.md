---
title: "BPREQI_FIELDS90 | Microsoft Docs"
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
  - "BPREQI_FIELDS90 (enumeración)"
ms.assetid: bf6f7efc-39f2-46a2-906d-c3647bf89995
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# BPREQI_FIELDS90
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Muestra los valores válidos que especifican información que se recupere sobre una solicitud de punto de interrupción.  esta enumeración extiende la enumeración de [BPREQI\_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) .  
  
## Sintaxis  
  
```cpp#  
enum enum_BPREQI_FIELDS90  
{  
   // VS 8.0 values  
   BPREQI90_BPLOCATION                = 0x0001,  
   BPREQI90_LANGUAGE                  = 0x0002,  
   BPREQI90_PROGRAM                   = 0x0004,  
   BPREQI90_PROGRAMNAME               = 0x0008,  
   BPREQI90_THREAD                    = 0x0010,  
   BPREQI90_THREADNAME                = 0x0020,  
   BPREQI90_PASSCOUNT                 = 0x0040,  
   BPREQI90_CONDITION                 = 0x0080,  
   BPREQI90_FLAGS                     = 0x0100,  
   BPREQI90_ALLOLDFIELDS              = 0x01ff,  
   BPREQI90_VENDOR                    = 0x0200,  
   BPREQI90_CONSTRAINT                = 0x0400,  
   BPREQI90_TRACEPOINT                = 0x0800,  
  
   // Values added in VS 9.0  
   BPREQI90_MACROTRACEPOINT           = 0x1000,  
  
   BPREQI90_ALLFIELDS                 = 0xffff  
};  
typedef DWORD BPREQI_FIELDS90;  
```  
  
```c#  
public enum enum_BPREQI_FIELDS90  
{  
    // VS 8.0 values  
    BPREQI90_BPLOCATION                = 0x0001,  
    BPREQI90_LANGUAGE                  = 0x0002,  
    BPREQI90_PROGRAM                   = 0x0004,  
    BPREQI90_PROGRAMNAME               = 0x0008,  
    BPREQI90_THREAD                    = 0x0010,  
    BPREQI90_THREADNAME                = 0x0020,  
    BPREQI90_PASSCOUNT                 = 0x0040,  
    BPREQI90_CONDITION                 = 0x0080,  
    BPREQI90_FLAGS                     = 0x0100,  
    BPREQI90_ALLOLDFIELDS              = 0x01ff,  
    BPREQI90_VENDOR                    = 0x0200,  
    BPREQI90_CONSTRAINT                = 0x0400,  
    BPREQI90_TRACEPOINT                = 0x0800,  
  
    // Values added in VS 9.0  
    BPREQI90_MACROTRACEPOINT           = 0x1000,  
  
    BPREQI90_ALLFIELDS                 = 0xffff  
};  
```  
  
#### Parámetros  
 BPREQI90\_BPLOCATION  
 Inicialice o utilice el campo de `bpLocation` \(ubicación de punto de interrupción\) de la estructura de [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) o de [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) .  
  
 BPREQI90\_LANGUAGE  
 Inicialice o utilice el campo de `guidLanguage` de la estructura de `BP_REQUEST_INFO` o de `BP_REQUEST_INFO2` .  
  
 BPREQI90\_PROGRAM  
 Inicialice o utilice el campo de `pProgram` de la estructura de `BP_REQUEST_INFO` o de `BP_REQUEST_INFO2` .  
  
 BPREQI90\_PROGRAMNAME  
 Inicialice o utilice el campo de `bstrProgramName` de la estructura de `BP_REQUEST_INFO` o de `BP_REQUEST_INFO2` .  
  
 BPREQI90\_THREAD  
 Inicialice o utilice el campo de `pThread` de la estructura de `BP_REQUEST_INFO` o de `BP_REQUEST_INFO2` .  
  
 BPREQI90\_THREADNAME  
 Inicialice o utilice el campo de `bstrThreadName` de la estructura de `BP_REQUEST_INFO` o de `BP_REQUEST_INFO2` .  
  
 BPREQI90\_PASSCOUNT  
 Inicialice o utilice el campo de `bpPassCount` de la estructura de `BP_REQUEST_INFO` o de `BP_REQUEST_INFO2` .  
  
 BPREQI90\_CONDITION  
 Inicialice o utilice el campo de `bpCondition` \(condición de punto de interrupción\) de la estructura de `BP_REQUEST_INFO` o de `BP_REQUEST_INFO2` .  
  
 BPREQI90\_FLAGS  
 Inicialice o utilice el campo de `dwFlags` de la estructura de `BP_REQUEST_INFO` o de `BP_REQUEST_INFO2` .  
  
 BPREQI90\_ALLOLDFIELDS  
 Inicialice o utilice todos los campos de la estructura de `BP_REQUEST_INFO` .  
  
 BPREQI90\_VENDOR  
 Inicialice o utilice el campo de `guidVendor` de la estructura de `BP_REQUEST_INFO2` .  
  
 BPREQI90\_CONSTRAINT  
 Inicialice o utilice el campo de `bstrConstraint` de la estructura de `BP_REQUEST_INFO2` .  
  
 BPREQI90\_TRACEPOINT  
 Inicialice o utilice el campo de `bstrTracepoint` de la estructura de `BP_REQUEST_INFO2` .  
  
 BPREQI90\_MACROTRACEPOINT  
 Inicialice o utilice el campo de `bstrMacroTracepoint` de la estructura de `BP_REQUEST_INFO2` .  BPREQI\_ALLFIELDS no incluye este campo.  
  
 BPREQI90\_ALLFIELDS  
 Especifica todos los campos de la estructura de `BP_REQUEST_INFO2` .  
  
## Requisitos  
 encabezado: Msdbg90.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)