---
title: "FIELD_INFO_FIELDS | Microsoft Docs"
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
  - "FIELD_INFO_FIELDS"
helpviewer_keywords: 
  - "Enumeración FIELD_INFO_FIELDS"
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# FIELD_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Especifica qué información se va a recuperar información sobre un objeto de [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .  
  
## Sintaxis  
  
```cpp#  
enum enum_FIELD_INFO_FIELDS {   
   FIF_FULLNAME  = 0x0001,  
   FIF_NAME      = 0x0002,  
   FIF_TYPE      = 0x0004,  
   FIF_MODIFIERS = 0x0008,  
   FIF_ALL       = 0xffffffff,  
   FIF_NONE      = 0x0000  
};  
typedef DWORD FIELD_INFO_FIELDS;  
```  
  
```c#  
public enum enum_FIELD_INFO_FIELDS {  
   FIF_FULLNAME  = 0x0001,  
   FIF_NAME      = 0x0002,  
   FIF_TYPE      = 0x0004,  
   FIF_MODIFIERS = 0x0008,  
   FIF_ALL       = 0xffffffff,  
   FIF_NONE      = 0x0000  
};  
```  
  
## Members  
 FIF\_FULLNAME  
 Inicializa y usan el campo de `bstrFullName` en la estructura de [FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md) .  
  
 FIF\_NAME  
 Inicializa y usan el campo de `bstrName` en la estructura de `FIELD_INFO` .  
  
 FIF\_TYPE  
 Inicializa y usan el campo de `bstrType` en la estructura de `FIELD_INFO` .  
  
 FIF\_MODIFIERS  
 Inicializa y usan el campo de `bstrModifiers` en la estructura de `FIELD_INFO` .  
  
## Comentarios  
 Esta configuración también se pasan como argumento al método de [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) para especificar qué campos de la estructura de [FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md) se deben inicializar.  
  
 Esta configuración también se utilizan en el miembro de `dwFields` de la estructura de `FIELD_INFO` para indicar qué campos son utilizados y válidos.  
  
 Estos marcadores se pueden combinar con `OR`bit a bit.  
  
## Requisitos  
 encabezado: sh.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)