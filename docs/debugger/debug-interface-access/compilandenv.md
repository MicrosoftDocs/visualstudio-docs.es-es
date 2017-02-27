---
title: "CompilandEnv | Microsoft Docs"
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
  - "CompilandEnv (símbolo)"
ms.assetid: 808404bb-ece1-47f1-b9ea-c76d4d86ddd9
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# CompilandEnv
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

el compilador puede incluir variables de entorno adicionales con símbolos.  Hay un token de `SymTagCompilandEnv` para cada una de estas variables.  
  
## Propiedades  
 La tabla siguiente se muestran las propiedades que son válidas para este tipo de token.  
  
|Propiedad.|Tipo de datos|Descripción|  
|----------------|-------------------|-----------------|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Símbolo para el compilando primario.|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Identificador del token primario léxico.|  
|[IDiaSymbol::get\_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Nombre de la variable.|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Id. de índice de símbolos.|  
|[IDiaSymbol::get\_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|devuelve `SymTagCompilandEnv` \(uno de los valores de [SymTagEnum \(Enumeración\)](../../debugger/debug-interface-access/symtagenum.md) \).|  
|[IDiaSymbol::get\_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|`VARIANT`|contenido Cadena\-valorados de la variable \(`VT_BSTR`\).|  
  
## Vea también  
 [Compiland](../../debugger/debug-interface-access/compiland.md)   
 [Jerarquía léxica de tipos de símbolos](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)