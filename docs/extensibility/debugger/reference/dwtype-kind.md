---
title: "dwTYPE_KIND | Microsoft Docs"
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
  - "dwTYPE_KIND"
helpviewer_keywords: 
  - "dwTYPE_KIND (enumeración)"
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# dwTYPE_KIND
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

especifica cómo interpretar el tipo de un objeto de [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .  
  
## Sintaxis  
  
```cpp#  
enum enum_dwTYPE_KIND {  
   TYPE_KIND_METADATA = 0x0001,  
   TYPE_KIND_PDB      = 0x0002,  
   TYPE_KIND_BUILT    = 0x0003,  
};  
  
typedef DWORD dwTYPE_KIND;  
```  
  
```c#  
public enum enum_dwTYPE_KIND {  
   TYPE_KIND_METADATA = 0x0001,  
   TYPE_KIND_PDB      = 0x0002,  
   TYPE_KIND_BUILT    = 0x0003,  
};  
```  
  
#### Parámetros  
 TYPE\_KIND\_METADATA  
 La combinación de [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md) debe interpretarse como estructura de [METADATA\_TYPE](../../../extensibility/debugger/reference/metadata-type.md) .  
  
 TYPE\_KIND\_PDB  
 La combinación de `TYPE_INFO` debe interpretarse como estructura de [PDB\_TYPE](../../../extensibility/debugger/reference/pdb-type.md) .  
  
 TYPE\_KIND\_BUILT  
 La combinación de `TYPE_INFO` debe interpretarse como estructura de [BUILT\_TYPE](../../../extensibility/debugger/reference/built-type.md) .  
  
## Comentarios  
 Los valores de esta enumeración aparecen en el campo de `dwKind` de la estructura de [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md) y se utilizan para determinar cómo interpretar al miembro de unión de `type` .  La estructura de `TYPE_INFO` es devuelta por una llamada al método de [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) .  
  
## Requisitos  
 encabezado: sh.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA\_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB\_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT\_TYPE](../../../extensibility/debugger/reference/built-type.md)