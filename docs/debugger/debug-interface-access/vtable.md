---
title: "VTable | Microsoft Docs"
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
  - "VTable (símbolo)"
  - "tablas virtuales"
ms.assetid: c8be6692-7d2a-4721-99d3-8e2e565bb8a1
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# VTable
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La tabla virtual se identifica mediante el símbolo de `SymTagVTable` .  
  
## Propiedades  
 La tabla siguiente se muestran las propiedades válidas adicionales para este tipo de token.  
  
|Propiedad.|Tipo de datos|Descripción|  
|----------------|-------------------|-----------------|  
|[IDiaSymbol::get\_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|símbolo de la clase que posee este VTable.|  
|[IDiaSymbol::get\_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|Identificador del elemento primario de la clase.|  
|[IDiaSymbol::get\_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` si la clase de VTable se marca como constante.|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Símbolo de compilación envolvente.|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Identificador del token primario léxico.|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Id. de índice de símbolos.|  
|[IDiaSymbol::get\_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|devuelve `SymTagVTable` \(uno de los valores de [SymTagEnum \(Enumeración\)](../../debugger/debug-interface-access/symtagenum.md) \).|  
|[IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Símbolo para [VTableShape](../../debugger/debug-interface-access/vtableshape.md)de VTable.|  
|[IDiaSymbol::get\_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|Identificador del tipo.|  
|[IDiaSymbol::get\_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` si la clase de VTable es sin alinear.|  
|[IDiaSymbol::get\_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` si la clase de VTable se marca como tal.|  
  
## Vea también  
 [Jerarquía de clases de tipos de símbolos](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [VTableShape](../../debugger/debug-interface-access/vtableshape.md)