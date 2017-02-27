---
title: "IDiaEnumSymbolsByAddr::Next | Microsoft Docs"
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
  - "IDiaEnumSymbolsByAddr::Next (método)"
ms.assetid: a1320587-7ce7-401f-9548-2f8bcece5cc3
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumSymbolsByAddr::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera los símbolos siguientes en orden de dirección.  
  
## Sintaxis  
  
```cpp#  
HRESULT Next (   
   ULONG        celt,   
   IDiaSymbol** rgelt,  
   ULONG*       pceltFetched  
);  
```  
  
#### Parámetros  
 celt  
 \[in\]  el número de símbolos en el enumerador que se recuperará.  
  
 rgelt  
 \[out\]  Una matriz que debe ser completo con el objeto de [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) que representa los símbolos deseados.  
  
 pceltFetched  
 \[out\]  devuelve el número de símbolos en el enumerador capturado.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`.  devuelve `S_FALSE` si no hay símbolos.  De lo contrario, devuelve un código de error.  
  
## Comentarios  
 Este método actualiza la posición del enumerador por el número de elementos capturados.  
  
## Vea también  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)