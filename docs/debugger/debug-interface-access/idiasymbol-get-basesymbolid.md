---
title: "IDiaSymbol::get_baseSymbolId | Microsoft Docs"
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
ms.assetid: cd504d2b-194f-4106-8de5-2de827a79cbd
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::get_baseSymbolId
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera el id. del token del que se basa el puntero.  
  
## Sintaxis  
  
```cpp  
HRESULT get_baseSymbolId(   
   DWORD *pRetVal);  
```  
  
#### Parámetros  
 `pRetVal`  
 \[out\] puntero A `DWORD` que contiene el id. del token del que se basa el puntero.  
  
## Valor devuelto  
 Si es correcto, especificado `S_OK`; si no, especificado `S_FALSE` o un código de error.  
  
## Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get\_baseSymbol](../../debugger/debug-interface-access/idiasymbol-get-basesymbol.md)