---
title: "IDiaSymbol::getSrcLineOnTypeDefn | Microsoft Docs"
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
ms.assetid: ad554d18-9988-4b64-ad71-e7594c266e94
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::getSrcLineOnTypeDefn
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera el archivo de código fuente y el número de línea que indica dónde se define un tipo definido por el usuario especificado.  
  
## Sintaxis  
  
```cpp  
HRESULT getSrcLineOnTypeDefn(  
   IDiaLineNumber **ppResult);  
```  
  
#### Parámetros  
 `ppResult`  
 \[out\] objeto de A `IDiaLineNumber` que contiene el archivo de código fuente y el número de línea donde el definido por el usuario.  
  
## Valor devuelto  
 Si es correcto, especificado `S_OK`; si no, especificado `S_FALSE` o un código de error.  
  
## Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)