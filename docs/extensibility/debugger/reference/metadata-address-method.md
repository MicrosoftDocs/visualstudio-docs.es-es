---
title: "METADATA_ADDRESS_METHOD | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "METADATA_ADDRESS_METHOD"
helpviewer_keywords: 
  - "Estructura METADATA_ADDRESS_METHOD"
ms.assetid: fc0e5370-1b4f-4867-837f-0d63c4b9dd09
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# METADATA_ADDRESS_METHOD
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta estructura representa la dirección de un método de una clase.  
  
## Sintaxis  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_METHOD {  
   _mdToken tokMethod;  
   DWORD    dwOffset;  
   DWORD    dwVersion;  
} METADATA_ADDRESS_METHOD;  
```  
  
```c#  
public struct METADATA_ADDRESS_METHOD {  
   public int  tokMethod;  
   public uint dwOffset;  
   public uint dwVersion;  
}  
```  
  
## términos  
 tokMethod  
 El identificador del método.  
  
 \[C\+\+\] `_mdToken` es `typedef` para `int`de 32 bits.  
  
 dwOffset  
 El desplazamiento inicial de la clase a este método \(puede representar el desplazamiento en el vtable\).  
  
 dwVersion  
 La versión del método \(este valor es único al proveedor del token\).  
  
## Comentarios  
 Esta estructura es parte de la combinación en la estructura de [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md) cuando el campo de `dwKind` de la estructura de `DEBUG_ADDRESS_UNION` se establece en `ADDRESS_KIND_METHOD` \(un valor de enumeración de [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md) \).  
  
## Requisitos  
 encabezado: sh.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)