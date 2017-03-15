---
title: "IDiaSymbol::findChildrenExByVA | Microsoft Docs"
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
  - "IDiaSymbol::findChildrenExByVA"
ms.assetid: 29080009-36e4-4697-acd7-50f2e3e1bf1b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::findChildrenExByVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera los elementos secundarios de símbolos que son válidos en una dirección virtual especificada.  
  
## Sintaxis  
  
```cpp#  
HRESULT findChildrenExByVA (   
   enum SymTagEnum   symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   DWORD             address,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### Parámetros  
 `symtag`  
 \[in\]  Especifica las etiquetas del token de los elementos secundarios que se recuperarán, como definido en [SymTagEnum \(Enumeración\)](../../debugger/debug-interface-access/symtagenum.md).  Establezca en `SymTagNull` para que todos los elementos secundarios se recuperen.  
  
 `name`  
 \[in\]  especifica el nombre de los elementos secundarios que se recuperarán.  Establezca en `NULL` para que todos los elementos secundarios se recuperen.  
  
 `compareFlags`  
 \[in\]  Especifica las opciones de comparación de aplicar para llamar a coincidir.  Los valores de enumeración de [NameSearchOptions \(Enumeración\)](../../debugger/debug-interface-access/namesearchoptions.md) sólo se pueden utilizar o en combinación.  
  
 `address`  
 \[in\]  Especifica la dirección virtual.  
  
 `ppResult`  
 \[out\]  Devuelve un objeto de [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) que contiene una lista de los símbolos secundarios recuperados.  
  
## Valor devuelto  
 Devuelve `S_OK` si por lo menos se encontró un elemento secundario de símbolos, o devuelve `S_FALSE` si no se encuentra ningún elementos secundarios; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Los símbolos locales que son información activa devuelta de intervalo de inclusión.  
  
## Requisitos  
 encabezado: Dia2.h  
  
 biblioteca: diaguids.lib  
  
 DLL: msdia100.dll  
  
## Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum \(Enumeración\)](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [NameSearchOptions \(Enumeración\)](../../debugger/debug-interface-access/namesearchoptions.md)