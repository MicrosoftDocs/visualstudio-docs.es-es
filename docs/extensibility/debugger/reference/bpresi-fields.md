---
title: "BPRESI_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BPRESI_FIELDS"
helpviewer_keywords: 
  - "Enumeración BPRESI_FIELDS"
ms.assetid: 99f17b1e-3e67-4f85-89d6-5c6cf45c8008
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# BPRESI_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Especifica la información que se recupere sobre la resolución correcta de un punto de interrupción.  
  
## Sintaxis  
  
```cpp#  
enum enum_BPRESI_FIELDS {   
   BPRESI_BPRESLOCATION = 0x0001,  
   BPRESI_PROGRAM       = 0x0002,  
   BPRESI_THREAD        = 0x0004,  
   BPRESI_ALLFIELDS     = 0xffffffff  
};  
typedef DWORD BPRESI_FIELDS;  
```  
  
```c#  
public enum enum_BPRESI_FIELDS {   
   BPRESI_BPRESLOCATION = 0x0001,  
   BPRESI_PROGRAM       = 0x0002,  
   BPRESI_THREAD        = 0x0004,  
   BPRESI_ALLFIELDS     = 0xffffffff  
};  
```  
  
## Members  
 BPRESI\_BPRESLOCATION  
 Inicializa y usan el campo de `bpResLocation` \(ubicación de resolución de punto de interrupción\) de la estructura de [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) .  
  
 BPRESI\_PROGRAM  
 Inicializa y usan el campo de `pProgram` de la estructura de `BP_RESOLUTION_INFO` .  
  
 BPRESI\_THREAD  
 Inicializa y usan el campo de `pThread` de la estructura de `BP_RESOLUTION_INFO` .  
  
 BPRESI\_ALLFIELDS  
 especifica todos los campos.  
  
## Comentarios  
 Pasado a [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) el método para indicar qué campos de la estructura de [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) se deben inicializar.  
  
 Estos marcadores también se utilizan para indicar qué campos de la estructura de `BP_RESOLUTION_INFO` son utilizados y válidos cuando se devuelve esa estructura.  
  
 estos valores se pueden combinar con `OR`bit a bit.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)