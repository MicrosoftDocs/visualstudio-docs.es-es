---
title: "DEBUGREF_INFO_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DEBUGREF_INFO_FLAGS"
helpviewer_keywords: 
  - "Enumeración DEBUGREF_INFO_FLAGS"
ms.assetid: 1b043327-302a-4f6d-b51d-f94f9d7c7f9d
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# DEBUGREF_INFO_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Especifica qué información se va a recuperar sobre un objeto de referencia de depuración.  
  
## Sintaxis  
  
```cpp#  
enum enum_DEBUGREF_INFO_FLAGS {   
   DEBUGREF_INFO_NAME             = 0x00000001,  
   DEBUGREF_INFO_TYPE             = 0x00000002,  
   DEBUGREF_INFO_VALUE            = 0x00000004,  
   DEBUGREF_INFO_ATTRIB           = 0x00000008,  
   DEBUGREF_INFO_REFTYPE          = 0x00000010,  
   DEBUGREF_INFO_REF              = 0x00000020,  
   DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,  
   DEBUGREF_INFO_NONE             = 0x00000000,  
   DEBUGREF_INFO_ALL              = 0xffffffff  
};  
typedef DWORD DEBUGREF_INFO_FLAGS;  
```  
  
```c#  
public enum enum_DEBUGREF_INFO_FLAGS {   
   DEBUGREF_INFO_NAME             = 0x00000001,  
   DEBUGREF_INFO_TYPE             = 0x00000002,  
   DEBUGREF_INFO_VALUE            = 0x00000004,  
   DEBUGREF_INFO_ATTRIB           = 0x00000008,  
   DEBUGREF_INFO_REFTYPE          = 0x00000010,  
   DEBUGREF_INFO_REF              = 0x00000020,  
   DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,  
   DEBUGREF_INFO_NONE             = 0x00000000,  
   DEBUGREF_INFO_ALL              = 0xffffffff  
};  
```  
  
## Members  
 DEBUGREF\_INFORMATION\_NAME  
 Inicializa y usan el campo de `bstrName` en la estructura.  
  
 DEBUGREF\_INFORMATION\_TYPE  
 Inicializa y usan el campo de `bstrType` en la estructura.  
  
 DEBUGREF\_INFORMATION\_VALUE  
 Inicializa y usan el campo de `bstrValue` en la estructura.  
  
 DEBUGREF\_INFORMATION\_ATTRIB  
 Inicializa y usan el campo de`dwAttrib` en la estructura.  
  
 DEBUGREF\_INFORMATION\_REFTYPE  
 Inicializa y usan el campo de `dwRefType` en la estructura.  
  
 DEBUGREF\_INFORMATION\_REF  
 Inicializa y usan el campo de `pReference` en la estructura.  
  
 DEBUGREF\_INFORMATION\_VALUE\_AUTOEXPAND  
 El campo value debe contener el valor auto\-expandido, si está disponible, para este tipo de objeto.  
  
 DEBUGREF\_INFORMATION\_NONE  
 Indica que no se establece ningún marcador.  
  
 DEBUGREF\_INFORMATION\_ALL  
 Indica una máscara de marcadores.  
  
## Comentarios  
 Estos marcadores se pasan a los métodos de [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) y de [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) para indicar qué campos de la estructura de [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) se deben inicializar.  
  
 utilizado para el miembro de `dwFields` de la estructura de `DEBUG_REFERENCE_INFO` para indicar qué campos son utilizados y válido cuando se devuelve la estructura.  
  
 estos valores se pueden combinar con `OR`bit a bit.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)   
 [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)