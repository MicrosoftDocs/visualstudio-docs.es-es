---
title: "Enumeraci&#243;n (Debug Interface Access SDK) | Microsoft Docs"
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
  - "tipos enumerados como símbolos"
  - "Enum (símbolo)"
ms.assetid: c777e2e6-88be-435b-b632-8d43f42b0b49
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Enumeraci&#243;n (Debug Interface Access SDK)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Las enumeraciones se identifican mediante los símbolos de `SymTagEnum` .  Cada valor de enumeración aparece como elemento secundario de clase con una etiqueta de `SymTagConstant` .  
  
## Propiedades  
 La tabla siguiente se muestran las propiedades válidas adicionales para este tipo de token.  
  
|Propiedad.|Tipo de datos|Descripción|  
|----------------|-------------------|-----------------|  
|[IDiaSymbol::get\_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)|`DWORD`|Uno de los valores de [BasicType \(Enumeración\)](../../debugger/debug-interface-access/basictype.md).|  
|[IDiaSymbol::get\_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|elemento primario de la clase de esta enumeración, si la hay.|  
|[IDiaSymbol::get\_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|Identificador del elemento primario de la clase.|  
|[IDiaSymbol::get\_constructor](../../debugger/debug-interface-access/idiasymbol-get-constructor.md)|`BOOL`|`TRUE` si la enumeración tiene un constructor.|  
|[IDiaSymbol::get\_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` si la enumeración se marca como const.|  
|[IDiaSymbol::get\_hasAssignmentOperator](../../debugger/debug-interface-access/idiasymbol-get-hasassignmentoperator.md)|`BOOL`|`TRUE` si la enumeración tiene un operador de asignación.|  
|[IDiaSymbol::get\_hasCastOperator](../../debugger/debug-interface-access/idiasymbol-get-hascastoperator.md)|`BOOL`|`TRUE` si la enumeración tiene un operador de conversión.|  
|[IDiaSymbol::get\_hasNestedTypes](../../debugger/debug-interface-access/idiasymbol-get-hasnestedtypes.md)|`BOOL`|`TRUE` si la enumeración tiene tipos anidados.|  
|[IDiaSymbol::get\_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`DWORD`|longitud de esta enumeración en bytes.|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Símbolo de [Compiland](../../debugger/debug-interface-access/compiland.md)envolvente.|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Identificador del token primario léxico.|  
|[IDiaSymbol::get\_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Nombre del tipo enumerado.|  
|[IDiaSymbol::get\_nested](../../debugger/debug-interface-access/idiasymbol-get-nested.md)|`BOOL`|`TRUE` si se anida la enumeración.|  
|[IDiaSymbol::get\_overloadedOperator](../../debugger/debug-interface-access/idiasymbol-get-overloadedoperator.md)|`BOOL`|`TRUE` si la enumeración tiene algunos operadores sobrecargados.|  
|[IDiaSymbol::get\_packed](../../debugger/debug-interface-access/idiasymbol-get-packed.md)|`BOOL`|`TRUE` si se empaqueta la enumeración.|  
|[IDiaSymbol::get\_scoped](../../debugger/debug-interface-access/idiasymbol-get-scoped.md)|`BOOL`|`TRUE` si la enumeración aparece en un ámbito léxico nonglobal.|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Id. de índice de símbolos.|  
|[IDiaSymbol::get\_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|devuelve `SymTagEnum` \(uno de los valores de [SymTagEnum \(Enumeración\)](../../debugger/debug-interface-access/symtagenum.md) \).|  
|[IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Símbolo para su tipo subyacente.|  
|[IDiaSymbol::get\_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|Identificador del tipo.|  
|[IDiaSymbol::get\_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` si la enumeración es sin alinear.|  
|[IDiaSymbol::get\_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` si la enumeración se marca como tal.|  
  
## Vea también  
 [Jerarquía de clases de tipos de símbolos](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)