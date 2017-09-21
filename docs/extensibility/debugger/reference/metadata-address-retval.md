---
title: "METADATA_ADDRESS_RETVAL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "METADATA_ADDRESS_RETVAL"
helpviewer_keywords: 
  - "Estructura METADATA_ADDRESS_RETVAL"
ms.assetid: 5b0ec0fb-84b3-4ce7-8e24-becf3d881d7d
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# METADATA_ADDRESS_RETVAL
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta estructura representa un valor devuelto de un método o función.  
  
## Sintaxis  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_RETVAL {  
   _mdToken tokMethod;  
   DWORD    dwCorType;  
   DWORD    dwSigSize;  
   BYTE     rgSig[10];  
} METADATA_ADDRESS_RETVAL;  
```  
  
```c#  
public struct METADATA_ADDRESS_RETVAL {  
   public int    tokMethod;  
   public uint   dwCorType;  
   public uint   dwSigSize;  
   public byte[] rgSig;  
}  
```  
  
## Términos  
 tokMethod  
 El identificador del método el valor devuelto es de.  
  
 dwCorType  
 El tipo base del valor devuelto. Se trata de un valor de la `CorElementType` enumeración definida en el [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] archivo corhdr.h SDK.  
  
 dwSigSize  
 El tamaño de la firma del valor devuelto \(tal como se almacena en `rgSig`\).  
  
 rgSig  
 Una matriz de bytes que forman la firma del valor devuelto.  
  
## Comentarios  
 Esta estructura es parte de la unión en el [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md) estructura cuando el `dwKind` campo de la `DEBUG_ADDRESS_UNION` estructura se establece en `ADDRESS_KIND_RETVAL` \(un valor de la [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md) \(enumeración\)\).  
  
## Requisitos  
 Encabezado: sh.h  
  
 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)