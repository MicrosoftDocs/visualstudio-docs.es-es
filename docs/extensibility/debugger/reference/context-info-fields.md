---
title: "CONTEXT_INFO_FIELDS | Microsoft Docs"
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
  - "CONTEXT_INFO_FIELDS"
helpviewer_keywords: 
  - "Enumeración CONTEXT_INFO_FIELDS"
ms.assetid: ef436bd3-738e-47e8-828c-8febce752439
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# CONTEXT_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Especifica qué información se va a recuperar sobre un contexto de memoria.  
  
## Sintaxis  
  
```cpp#  
enum enum_CONTEXT_INFO_FIELDS {   
   CIF_MODULEURL =       0x00000001,  
   CIF_FUNCTION =        0x00000002,  
   CIF_FUNCTIONOFFSET =  0x00000004,  
   CIF_ADDRESS =         0x00000008,  
   CIF_ADDRESSOFFSET =   0x00000010,  
   CIF_ADDRESSABSOLUTE = 0x00000020,  
   CIF_ALLFIELDS =       0x0000003f  
};  
typedef DWORD CONTEXT_INFO_FIELDS;  
```  
  
```c#  
public enum enum_CONTEXT_INFO_FIELDS {  
   CIF_MODULEURL =       0x00000001,  
   CIF_FUNCTION =        0x00000002,  
   CIF_FUNCTIONOFFSET =  0x00000004,  
   CIF_ADDRESS =         0x00000008,  
   CIF_ADDRESSOFFSET =   0x00000010,  
   CIF_ADDRESSABSOLUTE = 0x00000020,  
   CIF_ALLFIELDS =       0x0000003f  
};  
```  
  
## Members  
 CIF\_MODULEURL  
 Inicializa y usan el campo de `bstrModuleUrl` de la estructura de [CONTEXT\_INFO](../../../extensibility/debugger/reference/context-info.md) .  
  
 CIF\_FUNCTION  
 Inicializa y usan el campo de `bstrFunction` de la estructura de `CONTEXT_INFO` .  
  
 CIF\_FUNCTIONOFFSET  
 Inicializa y usan el campo de `posFunctionOffset` de la estructura de `CONTEXT_INFO` .  
  
 CIF\_ADDRESS  
 Inicializa y usan el campo de `bstrAddress` de la estructura de `CONTEXT_INFO` .  
  
 CIF\_ADDRESSOFFSET  
 Inicializa y usan el campo de `bstrAddressOffset` de la estructura de `CONTEXT_INFO` .  
  
 CIF\_ALLFIELDS  
 Inicializa y el uso todos los campos de la estructura de `CONTEXT_INFO` .  
  
## Comentarios  
 Estos valores se pasa un parámetro al método de [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) para indicar qué campos de la estructura de [CONTEXT\_INFO](../../../extensibility/debugger/reference/context-info.md) se deben inicializar.  
  
 Estos marcadores también se utilizan para indicar qué campos de la estructura de `CONTEXT_INFO` son utilizados y válidos cuando se devuelve la estructura.  
  
 Estos valores se pueden combinar con una operación OR bit a bit.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [CONTEXT\_INFO](../../../extensibility/debugger/reference/context-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)