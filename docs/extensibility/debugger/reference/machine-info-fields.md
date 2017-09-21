---
title: "MACHINE_INFO_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MACHINE_INFO_FIELDS"
helpviewer_keywords: 
  - "Enumeración MACHINE_INFO_FIELDS"
ms.assetid: 2d61d206-7d40-4df1-8c88-1b3c9c78821e
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# MACHINE_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Especifica qué tipo de información a recuperar en un equipo determinado.  
  
## Sintaxis  
  
```cpp#  
enum enum_MACHINE_INFO_FIELDS {   
   MCIF_NAME  = 0x00000001,  
   MCIF_FLAGS = 0x00000002,  
   MCIF_ALL   = 0x00000003  
};  
typedef DWORD MACHINE_INFO_FIELDS;  
```  
  
```c#  
public enum enum_MACHINE_INFO_FIELDS {   
   MCIF_NAME  = 0x00000001,  
   MCIF_FLAGS = 0x00000002,  
   MCIF_ALL   = 0x00000003  
};  
```  
  
## Members  
 MCIF\_NAME  
 Inicializa y usan el campo de `bstrName` en la estructura.  
  
 MCIF\_FLAGS  
 Inicializa y usan el campo de `Flags` en la estructura.  
  
 MIF\_ALL  
 Inicializa y el uso de todos los campos de la estructura.  
  
## Comentarios  
 Estos valores se pasan al método de [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md) para indicar qué miembros de la estructura de [MACHINE\_INFO](../../../extensibility/debugger/reference/machine-info.md) se deben inicializar.  
  
 También se utiliza en el miembro de `Fields` de la estructura de `MACHINE_INFO` para indicar qué campos son utilizados y válidos.  
  
 Estos marcadores se pueden combinar con `OR`bit a bit.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MACHINE\_INFO](../../../extensibility/debugger/reference/machine-info.md)   
 [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)