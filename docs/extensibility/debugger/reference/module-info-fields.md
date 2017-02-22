---
title: "MODULE_INFO_FIELDS | Microsoft Docs"
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
  - "MODULE_INFO_FIELDS"
helpviewer_keywords: 
  - "Enumeración MODULE_INFO_FIELDS"
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# MODULE_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Especifica marcadores para la información de módulos de depuración.  
  
## Sintaxis  
  
```cpp#  
enum enum_MODULE_INFO_FIELDS {   
   MIF_NONE              = 0x0000,  
   MIF_NAME              = 0x0001,  
   MIF_URL               = 0x0002,  
   MIF_VERSION           = 0x0004,  
   MIF_DEBUGMESSAGE      = 0x0008,  
   MIF_LOADADDRESS       = 0x0010,  
   MIF_PREFFEREDADDRESS  = 0x0020,  
   MIF_SIZE              = 0x0040,  
   MIF_LOADORDER         = 0x0080,  
   MIF_TIMESTAMP         = 0x0100,  
   MIF_URLSYMBOLLOCATION = 0x0200,  
   MIF_FLAGS             = 0x0400,  
   MIF_ALLFIELDS         = 0x07ff  
};  
typedef DWORD MODULE_INFO_FIELDS;  
```  
  
```c#  
public enum enum_MODULE_INFO_FIELDS {   
   MIF_NONE              = 0x0000,  
   MIF_NAME              = 0x0001,  
   MIF_URL               = 0x0002,  
   MIF_VERSION           = 0x0004,  
   MIF_DEBUGMESSAGE      = 0x0008,  
   MIF_LOADADDRESS       = 0x0010,  
   MIF_PREFFEREDADDRESS  = 0x0020,  
   MIF_SIZE              = 0x0040,  
   MIF_LOADORDER         = 0x0080,  
   MIF_TIMESTAMP         = 0x0100,  
   MIF_URLSYMBOLLOCATION = 0x0200,  
   MIF_FLAGS             = 0x0400,  
   MIF_ALLFIELDS         = 0x07ff  
};  
```  
  
## Members  
 MIF\_NONE  
 Inicializa y el uso ninguno de los campos de la estructura.  
  
 MIF\_NAME  
 Inicializa y usan el campo de `m_bstrName` en la estructura de [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md) .  
  
 MIF\_URL  
 Inicializa y usan el campo de `m_bstrUrl` en la estructura de `MODULE_INFO` .  
  
 MIF\_VERSION  
 Inicializa y usan el campo de `m_bstrVersion` en la estructura de `MODULE_INFO` .  
  
 MIF\_DEBUGMESSAGE  
 Inicializa y usan el campo de `m_bstrDebugMessage` en la estructura de `MODULE_INFO` .  
  
 MIF\_LOADADDRESS  
 Inicializa y usan el campo de `m_addrLoadAddress` en la estructura de `MODULE_INFO` .  
  
 MIF\_PREFFEREDADDRESS  
 Inicializa y usan el campo de `m_addrPreferredLoadAddress` en la estructura de `MODULE_INFO` .  
  
 MIF\_SIZE  
 Inicializa y usan el campo de `m_dwSize` en la estructura de `MODULE_INFO` .  
  
 MIF\_LOADORDER  
 Inicializa y usan el campo de `m_dwLoadOrder` en la estructura de `MODULE_INFO` .  
  
 MIF\_TIMESTAMP  
 Inicializa y usan el campo de `m_TimeStamp` en la estructura de `MODULE_INFO` .  
  
 MIF\_URLSYMBOLLOCATION  
 Inicializa y usan el campo de `m_bstrUrlSymbolLocation` en la estructura de `MODULE_INFO` .  
  
 MIF\_FLAGS  
 Inicializa y usan el campo de `m_dwModuleFlags` en la estructura de `MODULE_INFO` .  
  
 MIF\_ALLFIELDS  
 Inicializa y el uso de todos los campos de la estructura de `MODULE_INFO` .  
  
## Comentarios  
 Estos valores se pasan como argumento al método de [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) para indicar qué campos de la estructura de [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md) se deben inicializar.  
  
 Esta configuración también se utilizan en la estructura de `MODULE_INFO` para indicar qué campos son utilizados y válidos.  
  
 Estos marcadores se pueden combinar con `OR`bit a bit.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)