---
title: "IDiaEnumLineNumbers::Next | Microsoft Docs"
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
  - "IDiaEnumLineNumbers::Next (método)"
ms.assetid: 363d5b40-1316-4ab8-836f-63637f619e0a
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumLineNumbers::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

recupera un número especificado de números de línea en la secuencia de la enumeración.  
  
## Sintaxis  
  
```cpp#  
HRESULT Next (   
   ULONG            celt,  
   IDiaLineNumber** rgelt,  
   ULONG*           pceltFetched  
);  
```  
  
#### Parámetros  
 celt  
 \[in\]  el número de números de línea en el enumerador que se recuperará.  
  
 rgelt  
 \[out\]  Devuelve una matriz de los objetos de [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) que representan números de línea deseados.  
  
 pceltFetched  
 \[out\]  devuelve el número de números de línea en el enumerador capturado.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`.  devuelve `S_FALSE` si no hay números de línea.  De lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)   
 [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)