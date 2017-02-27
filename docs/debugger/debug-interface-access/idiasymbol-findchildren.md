---
title: "IDiaSymbol::findChildren | Microsoft Docs"
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
  - "IDiaSymbol::findChildren (método)"
ms.assetid: 5fe7573a-e48b-428d-9c17-7421b7209246
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IDiaSymbol::findChildren
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera los elementos secundarios de símbolos.  
  
## Sintaxis  
  
```cpp#  
HRESULT findChildren (   
   enum SymTagEnum   symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### Parámetros  
 `symtag`  
 \[in\]  Especifica las etiquetas del token de los elementos secundarios que se recuperarán, como definido en [SymTagEnum \(Enumeración\)](../../debugger/debug-interface-access/symtagenum.md).  Establezca en `SymTagNull` para que todos los elementos secundarios se recuperen.  
  
 `name`  
 \[in\]  especifica el nombre de los elementos secundarios que se recuperarán.  Establezca en `NULL` para que todos los elementos secundarios se recuperen.  
  
 `compareFlags`  
 \[in\]  Especifica las opciones de comparación aplicado para llamar a coincidir.  Los valores de enumeración de [NameSearchOptions \(Enumeración\)](../../debugger/debug-interface-access/namesearchoptions.md) sólo se pueden utilizar o en combinación.  
  
 `ppResult`  
 \[out\]  Devuelve un objeto de [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) que contiene una lista de los símbolos secundarios recuperados.  
  
## Valor devuelto  
 Devuelve `S_OK` si por lo menos se encontró un elemento secundario de símbolos, o devuelve `S_FALSE` si no se encuentra ningún elementos secundarios; si no devuelve un código de error.  
  
## Comentarios  
 Este método es idéntico a llamar al método de [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md) con este símbolo como primer parámetro.  
  
## Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum \(Enumeración\)](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [NameSearchOptions \(Enumeración\)](../../debugger/debug-interface-access/namesearchoptions.md)