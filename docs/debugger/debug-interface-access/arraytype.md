---
title: "ArrayType | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ArrayType (símbolo)"
ms.assetid: 1d973a3a-2bde-46df-8625-85d519bb3cc9
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# ArrayType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Una matriz se identifica mediante un símbolo de `SymTagArray` .  
  
## Propiedades  
 La tabla siguiente se muestran las propiedades válidas adicionales para este tipo de token.  
  
|Propiedad.|Tipo de datos|Descripción|  
|----------------|-------------------|-----------------|  
|[IDiaSymbol::get\_arrayIndexType](../../debugger/debug-interface-access/idiasymbol-get-arrayindextype.md)|`IDiaSymbol*`|Token del tipo de índice de matriz.|  
|[IDiaSymbol::get\_arrayIndexTypeId](../../debugger/debug-interface-access/idiasymbol-get-arrayindextypeid.md)|`DWORD`|Identificador del tipo de índice de matriz.|  
|[IDiaSymbol::get\_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` si la matriz se marca como const.|  
|[IDiaSymbol::get\_count](../../debugger/debug-interface-access/idiasymbol-get-count.md)|`DWORD`|Número de elementos de la matriz.|  
|[IDiaSymbol::get\_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`LONGLONG`|Tamaño, en bytes, de esta matriz.|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Símbolo de compilación envolvente.|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Identificador del token primario léxico.|  
|[IDiaSymbol::get\_rank](../../debugger/debug-interface-access/idiasymbol-get-rank.md)|`DWORD`|Fila de una matriz multidimensional de FORTRAN.|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Id. de índice de símbolos.|  
|[IDiaSymbol::get\_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|devuelve `SymTagArray` \(uno de los valores de [SymTagEnum \(Enumeración\)](../../debugger/debug-interface-access/symtagenum.md) \).|  
|[IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Token del tipo de elemento de matriz.|  
|[IDiaSymbol::get\_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|Identificador del tipo de elemento de matriz.|  
|[IDiaSymbol::get\_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` si la matriz es sin alinear|  
|[IDiaSymbol::get\_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` si la matriz se marca como tal.|  
  
## Vea también  
 [Jerarquía de clases de tipos de símbolos](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [Dimensión](../../debugger/debug-interface-access/dimension.md)