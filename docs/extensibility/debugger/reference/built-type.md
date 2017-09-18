---
title: "BUILT_TYPE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BUILT_TYPE"
helpviewer_keywords: 
  - "Estructura BUILT_TYPE"
ms.assetid: cc02c32c-0f65-4210-ad25-a9b1899066e8
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# BUILT_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta estructura especifica información sobre un tipo de campo tomado de metadatos.  
  
## Sintaxis  
  
```cpp#  
typedef struct _tagTYPE_BUILT {  
   ULONG32      ulAppDomainID;  
   GUID         guidModule;  
   IDebugField* pUnderlyingField;  
} BUILT_TYPE;  
```  
  
```c#  
public struct BUILT_TYPE {  
   public uint        ulAppDomainID;  
   public Guid        guidModule;  
   public IDebugField pUnderlyingField;  
};  
```  
  
#### Parámetros  
 ulAppDomainID  
 Identificador de la aplicación que el símbolo procede.  Se utiliza para identificar una instancia de la aplicación.  
  
 guidModule  
 GUID del módulo que contiene este campo.  
  
 pUnderlyingField  
 Un objeto de [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que identifica el campo subyacente asociado a este campo integrado.  
  
## Comentarios  
 Esta estructura aparece como parte de la combinación en la estructura de [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md) cuando el campo de `dwKind` de la estructura de `TYPE_INFO` se establece en `TYPE_KIND_BUILT` \(un valor de enumeración de [dwTYPE\_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) \).  
  
## Requisitos  
 encabezado: sh.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE\_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)