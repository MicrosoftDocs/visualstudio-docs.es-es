---
title: "BPERESI_FIELDS | Microsoft Docs"
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
  - "BPERESI_FIELDS"
helpviewer_keywords: 
  - "Enumeración BPERESI_FIELDS"
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# BPERESI_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Especifica la información que se recupere sobre una resolución incorrecta de un punto de interrupción.  
  
## Sintaxis  
  
```cpp#  
enum enum_BPERESI_FIELDS {   
   PERESI_BPRESLOCATION = 0x0001,  
   BPERESI_PROGRAM      = 0x0002,  
   BPERESI_THREAD       = 0x0004,  
   BPERESI_MESSAGE      = 0x0008,  
   BPERESI_TYPE         = 0x0010,  
   BPERESI_ALLFIELDS    = 0xffffffff  
};  
typedef DWORD BPERESI_FIELDS;  
```  
  
```c#  
public enum enum_BPERESI_FIELDS {   
   PERESI_BPRESLOCATION = 0x0001,  
   BPERESI_PROGRAM      = 0x0002,  
   BPERESI_THREAD       = 0x0004,  
   BPERESI_MESSAGE      = 0x0008,  
   BPERESI_TYPE         = 0x0010,  
   BPERESI_ALLFIELDS    = 0xffffffff  
};  
```  
  
## Members  
 PERESI\_BPRESLOCATION  
 Inicializa y usan el campo de `bpResLocation` \(ubicación de resolución de punto de interrupción\) de la estructura de [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) .  
  
 BPERESI\_PROGRAM  
 Inicializa y usan el campo de `pProgram` de la estructura de `BP_ERROR_RESOLUTION_INFO` .  
  
 BPERESI\_THREAD  
 Inicializa y usan el campo de `pThread` de la estructura de `BP_ERROR_RESOLUTION_INFO` .  
  
 BPERESI\_MESSAGE  
 Inicializa y usan el campo de `bstrMessage` de la estructura de `BP_ERROR_RESOLUTION_INFO` .  
  
 BPERESI\_TYPE  
 Inicializa y usan el campo de `dwType` \(punto de interrupción tipo\) de la estructura de `BP_ERROR_RESOLUTION_INFO` .  
  
 BPERESI\_ALLFIELDS  
 Inicializa y el uso todos los campos de la estructura de `BP_ERROR_RESOLUTION_INFO` .  
  
## Comentarios  
 Pasado como un parámetro al método de [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) para indicar qué campos de la estructura de [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) se deben inicializar.  
  
 Esta configuración también se utilizan para indicar qué campos de la estructura de `BP_ERROR_RESOLUTION_INFO` son utilizados y válidos cuando se devuelve esa estructura.  
  
 estos valores se pueden combinar con `OR`bit a bit.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)