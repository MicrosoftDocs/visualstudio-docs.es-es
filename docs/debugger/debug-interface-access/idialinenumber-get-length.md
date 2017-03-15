---
title: "IDiaLineNumber::get_length | Microsoft Docs"
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
  - "IDiaLineNumber::get_length (método)"
ms.assetid: 2c55a6f7-4ef5-45fb-9fd1-d72deaaa2829
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaLineNumber::get_length
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

recupera el número de bytes en un bloque.  
  
## Sintaxis  
  
```cpp#  
HRESULT get_length (   
   DWORD* pRetVal  
);  
```  
  
#### Parámetros  
 `pRetVal`  
 \[out\]  devuelve el número de bytes en un bloque.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`.  devuelve `S_FALSE` si esta propiedad no se admite.  De lo contrario, devuelve un código de error.  
  
## Comentarios  
 El bloque es la longitud de código fuente en la línea como se representa por el objeto de [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) .  
  
## Vea también  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)