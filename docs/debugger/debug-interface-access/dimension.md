---
title: "Dimensi&#243;n | Microsoft Docs"
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
  - "Símbolo de dimensión"
ms.assetid: 94f791da-bfea-454f-8a14-da31e8e1596a
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Dimensi&#243;n
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cada matriz de FORTRAN tiene una dimensión que se identifica mediante un símbolo de `SymTagDimension` .  
  
## Propiedades  
 La tabla siguiente se muestran las propiedades válidas adicionales para este tipo de token.  
  
|Propiedad.|Tipo de datos|Descripción|  
|----------------|-------------------|-----------------|  
|[IDiaSymbol::get\_lowerBound](../../debugger/debug-interface-access/idiasymbol-get-lowerbound.md)|`IDiaSymbol*`|Límite inferior de una dimensión de la matriz de FORTRAN.|  
|[IDiaSymbol::get\_lowerBoundId](../../debugger/debug-interface-access/idiasymbol-get-lowerboundid.md)|`DWORD`|Identificador del símbolo bajo\-enlazado.|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Id. de índice de símbolos.|  
|[IDiaSymbol::get\_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|devuelve `SymTagDimension` \(uno de los valores de [SymTagEnum \(Enumeración\)](../../debugger/debug-interface-access/symtagenum.md) \).|  
|[IDiaSymbol::get\_upperBound](../../debugger/debug-interface-access/idiasymbol-get-upperbound.md)|`IDiaSymbol*`|Límite superior de una dimensión de la matriz de FORTRAN.|  
|[IDiaSymbol::get\_upperBoundId](../../debugger/debug-interface-access/idiasymbol-get-upperboundid.md)|`DWORD`|Identificador del símbolo de límite superior.|  
  
## Vea también  
 [ArrayType](../../debugger/debug-interface-access/arraytype.md)   
 [Jerarquía de clases de tipos de símbolos](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)