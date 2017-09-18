---
title: "METADATA_ADDRESS_LOCAL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "METADATA_ADDRESS_LOCAL"
helpviewer_keywords: 
  - "Estructura METADATA_ADDRESS_LOCAL"
ms.assetid: 635f6bc5-c486-4e0e-83db-36f15e543843
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# METADATA_ADDRESS_LOCAL
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta estructura representa la dirección de una variable local dentro de un ámbito \(normalmente una función o un método\).  
  
## Sintaxis  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_LOCAL {  
   _mdToken  tokMethod;  
   IUnknown* pLocal;  
   DWORD     dwIndex;  
} METADATA_ADDRESS_LOCAL;  
```  
  
```c#  
public struct METADATA_ADDRESS_LOCAL {  
   public int    tokMethod;  
   public object pLocal;  
   public uint   dwIndex;  
}  
```  
  
## términos  
 tokMethod  
 El identificador de método o función la variable local forma parte de.  
  
 \[C\+\+\] `_mdToken` es `typedef` para `int`de 32 bits.  
  
 pLocal  
 El token cuya dirección esta estructura representa.  
  
 dwIndex  
 Puede ser el índice de esta variable local en el método o la función, o algún otro valor \(específico del lenguaje\).  
  
## Comentarios  
 Esta estructura es parte de la combinación en la estructura de [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md) cuando el campo de `dwKind` de la estructura de `DEBUG_ADDRESS_UNION` se establece en `ADDRESS_KIND_LOCAL` \(un valor de enumeración de [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md) \).  
  
 `Warning:`\[sólo C\+\+\] si `pLocal` no es null, debe llamar a `Release` en el puntero token \(`addr` es un campo de la estructura de [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) \):  
  
```  
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL &&  addr.addr.addrLocal.pLocal != NULL)  
{  
    addr.addr.addrLocal.pLocal->Release();  
}  
```  
  
## Requisitos  
 encabezado: sh.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)