---
title: "CustomType | Microsoft Docs"
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
  - "CustomType (símbolo)"
ms.assetid: 1b66bc0a-7979-416f-bf7f-e5df91584c91
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# CustomType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

un símbolo de `SymTagCustomType` identifican los tipos Proveedor\-definido \(tipos compilador\-específicos\).  
  
## Propiedades  
 La tabla siguiente se muestran las propiedades válidas adicionales para este tipo de token.  
  
|Propiedad.|Tipo de datos|Descripción|  
|----------------|-------------------|-----------------|  
|[IDiaSymbol::get\_oemId](../../debugger/debug-interface-access/idiasymbol-get-oemid.md)|`DWORD`|Identificador OEM.|  
|[IDiaSymbol::get\_oemSymbolId](../../debugger/debug-interface-access/idiasymbol-get-oemsymbolid.md)|`DWORD`|La identificación interna OEM|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Id. de índice de símbolos.|  
|[IDiaSymbol::get\_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|devuelve `SymTagCustomType` \(uno de los valores de [SymTagEnum \(Enumeración\)](../../debugger/debug-interface-access/symtagenum.md) \).|  
|[IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|El primer tipo que hace referencia el símbolo de tipo personalizado.|  
|[IDiaSymbol::get\_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|Identificador del tipo.|  
|[IDiaSymbol::get\_types](../../debugger/debug-interface-access/idiasymbol-get-types.md)|`IDiaSymbol**`|Matriz de todos los tipos a los que hace referencia el símbolo de tipo personalizado.|  
  
## Vea también  
 [Jerarquía de clases de tipos de símbolos](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)