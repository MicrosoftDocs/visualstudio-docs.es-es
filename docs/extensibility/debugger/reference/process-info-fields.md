---
title: "PROCESS_INFO_FIELDS | Microsoft Docs"
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
  - "PROCESS_INFO_FIELDS"
helpviewer_keywords: 
  - "Enumeración PROCESS_INFO_FIELDS"
ms.assetid: 0d9cc345-3d3a-44d8-ae15-a67acb97a828
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# PROCESS_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Especifica qué tipo de información a recuperar en un proceso.  
  
## Sintaxis  
  
```cpp#  
enum enum_PROCESS_INFO_FIELDS {   
   PIF_FILE_NAME             = 0x00000001,  
   PIF_BASE_NAME             = 0x00000002,  
   PIF_TITLE                 = 0x00000004,  
   PIF_PROCESS_ID            = 0x00000008,  
   PIF_SESSION_ID            = 0x00000010,  
   PIF_ATTACHED_SESSION_NAME = 0x00000020,  
   PIF_CREATION_TIME         = 0x00000040,  
   PIF_FLAGS                 = 0x00000080,  
   PIF_ALL                   = 0x000000ff  
};  
typedef DWORD PROCESS_INFO_FIELDS;  
```  
  
```c#  
public enum enum_PROCESS_INFO_FIELDS {   
   PIF_FILE_NAME             = 0x00000001,  
   PIF_BASE_NAME             = 0x00000002,  
   PIF_TITLE                 = 0x00000004,  
   PIF_PROCESS_ID            = 0x00000008,  
   PIF_SESSION_ID            = 0x00000010,  
   PIF_ATTACHED_SESSION_NAME = 0x00000020,  
   PIF_CREATION_TIME         = 0x00000040,  
   PIF_FLAGS                 = 0x00000080,  
   PIF_ALL                   = 0x000000ff  
};  
```  
  
## Members  
 PIF\_FILE\_NAME  
 Inicializa y usan el campo de `bstrFileName` de la estructura de [PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md) .  
  
 PIF\_BASE\_NAME  
 Inicializa y usan el campo de `bstrBaseName` de la estructura de `PROCESS_INFO` .  
  
 PIF\_TITLE  
 Inicializa y usan el campo de `bstrTitle` de la estructura de `PROCESS_INFO` .  
  
 PIF\_PROCESS\_ID  
 Inicializa y usan el campo de `ProcessId` de la estructura de `PROCESS_INFO` .  
  
 PIF\_SESSION\_ID  
 Inicializa y usan el campo de `dwSessionId` de la estructura de `PROCESS_INFO` .  
  
 PIF\_ATTACHED\_SESSION\_NAME  
 Inicializa y usan el campo de `bstrAttachedSessionName` de la estructura de `PROCESS_INFO` .  
  
 PIF\_CREATION\_TIME  
 Inicializa y usan el campo de `CreationTime` de la estructura de `PROCESS_INFO` .  
  
 PIF\_FLAGS  
 Inicializa y usan el campo de `Flags` de la estructura de `PROCESS_INFO` .  
  
 PIF\_ALL  
 Finalice todos los campos.  
  
## Comentarios  
 Pasado a [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) el método para indicar qué campos de la estructura de [PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md) se deben inicializar.  
  
 También se utiliza en el campo de `Fields` de la estructura de `PROCESS_INFO` para indicar qué campos son utilizados y válidos.  
  
 Estos marcadores se pueden combinar con `OR`bit a bit.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md)