---
title: "FIELD_INFO | Microsoft Docs"
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
  - "FIELD_INFO"
helpviewer_keywords: 
  - "Estructura FIELD_INFO"
ms.assetid: bfafef6d-0c83-43d7-a779-1f0d24b166a1
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# FIELD_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta estructura describe la variable local, el parámetro, u otro campo.  
  
## Sintaxis  
  
```cpp#  
typedef struct _tagFieldInfo {   
   FIELD_INFO_FIELDS dwFields;  
   BSTR              bstrFullName;  
   BSTR              bstrName;  
   BSTR              bstrType;  
   FIELD_MODIFIERS   dwModifiers;  
} FIELD_INFO;  
```  
  
```c#  
public struct FIELD_INFO {  
   public uint   dwFields;  
   public string bstrFullName;  
   public string bstrName;  
   public string bstrType;  
   public uint   dwModifiers;  
};  
```  
  
## Members  
 dwFields  
 Una combinación de marcadores de enumeración de [FIELD\_INFO\_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) que especifica completan los integrantes.  
  
 bstrFullName  
 El nombre completo del campo.  
  
 bstrName  
 El nombre corto del campo.  
  
 bstrType  
 Tipo del campo.  
  
 dwModifiers  
 Una combinación de marcadores de enumeración de [FIELD\_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) que describe el campo.  
  
## Comentarios  
 Esta estructura se pasa al método de [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) donde se completa.  
  
## Requisitos  
 encabezado: sh.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [FIELD\_INFO\_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)   
 [FIELD\_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)