---
title: "METADATA_ADDRESS_ARRAYELEM | Microsoft Docs"
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
  - "METADATA_ADDRESS_ARRAYELEM"
helpviewer_keywords: 
  - "Estructura METADATA_ADDRESS_ARRAYELEM"
ms.assetid: 24321be5-7c17-4038-82a1-c20a2b68ff3c
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# METADATA_ADDRESS_ARRAYELEM
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta estructura representa un elemento de matriz dentro de una matriz.  
  
## Sintaxis  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_ARRAYELEM {  
   _mdToken tokMethod;  
   DWORD    dwIndex;  
} METADATA_ADDRESS_ARRAYELEM;  
```  
  
```c#  
public struct METADATA_ADDRESS_ARRAYELEM {  
   public int  tokMethod;  
   public uint dwIndex;  
}  
```  
  
## términos  
 tokMethod  
 El identificador de matriz este elemento es una parte de.  
  
 \[C\+\+\] `_mdToken` es `typedef` para `int`de 32 bits.  
  
 dwIndex  
 Índice de este elemento dentro de la matriz.  
  
## Comentarios  
 Esta estructura es parte de la combinación en la estructura de [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md) cuando el campo de `dwKind` de la estructura de `DEBUG_ADDRESS_UNION` se establece en `ADDRESS_KIND_ARRAYELEM` \(un valor de enumeración de [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md) \).  
  
## Requisitos  
 encabezado: sh.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)