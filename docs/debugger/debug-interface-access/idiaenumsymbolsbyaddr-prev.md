---
title: "IDiaEnumSymbolsByAddr::Prev | Microsoft Docs"
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
  - "IDiaEnumSymbolsByAddr::Prev (método)"
ms.assetid: da3b3dca-68cb-4cb0-b25c-e28a1ffe49d3
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumSymbolsByAddr::Prev
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera los símbolos anteriores en orden de dirección.  
  
## Sintaxis  
  
```cpp#  
HRESULT Prev (   
   ULONG        celt,   
   IDiaSymbol** rgelt,  
   ULONG*       pceltFetched  
);  
```  
  
#### Parámetros  
 celt  
 \[in\]  el número de símbolos en el enumerador que se recuperará.  
  
 rgelt  
 \[out\]  Una matriz que debe ser completo con objetos de [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) que representan los símbolos deseados.  
  
 pceltFetched  
 \[out\]  devuelve el número de símbolos en el enumerador capturado.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`.  devuelve `S_FALSE` si no hay símbolos anteriores.  De lo contrario, devuelve un código de error.  
  
## Comentarios  
 Este método actualiza la posición del enumerador por el número de elementos capturados.  
  
## Vea también  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)