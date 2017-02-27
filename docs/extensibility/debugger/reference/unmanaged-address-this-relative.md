---
title: "UNMANAGED_ADDRESS_THIS_RELATIVE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UNMANAGED_ADDRESS_THIS_RELATIVE"
helpviewer_keywords: 
  - "Estructura UNMANAGED_ADDRESS_THIS_RELATIVE"
ms.assetid: e6a91ace-2d47-4ff9-aefb-8d8b68eab0b2
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# UNMANAGED_ADDRESS_THIS_RELATIVE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta estructura representa una dirección relativa a un puntero de `this` \(`Me` en Visual Basic\).  
  
## Sintaxis  
  
```cpp  
typedef struct _tagUNMANAGED_THIS_RELATIVE {  
   DWORD dwOffset;  
   DWORD dwBitOffset;  
   DWORD dwBitLength;  
} UNMANAGED_ADDRESS_THIS_RELATIVE;  
```  
  
```c#  
public struct UNMANAGED_THIS_RELATIVE {  
   public uint dwOffset;  
   public uint dwBitOffset;  
   public uint dwBitLength;  
}  
```  
  
## términos  
 dwOffset  
 Desplazamiento de bytes de una posición base \(por ejemplo, inicio de una clase vtable\).  
  
 dwBitOffset  
 De en bits de una posición base \(siempre 0 a menos que hace referencia a un campo de bits\).  
  
 dwBitLength  
 Número de bits que representan la dirección \(siempre 0 a menos que hace referencia a un campo de bits\).  
  
## Comentarios  
 Esta estructura es parte de la combinación en la estructura de [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md) cuando el campo de `dwKind` de la estructura de `DEBUG_ADDRESS_UNION` se establece en `ADDRESS_KIND_UNMANAGED_THIS_RELATIVE` \(un valor de enumeración de [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md) \).  
  
## Requisitos  
 encabezado: sh.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)