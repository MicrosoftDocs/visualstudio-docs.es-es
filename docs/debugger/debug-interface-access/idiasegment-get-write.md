---
title: "IDiaSegment::get_write | Microsoft Docs"
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
  - "IDiaSegment::get_write (método)"
ms.assetid: 5fcda988-6be1-4b2f-8660-b59aa78fc35d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSegment::get_write
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera una marca que indica si el segmento puede modificarse.  
  
## Sintaxis  
  
```cpp#  
HRESULT get_write (   
   BOOL* pRetVal  
);  
```  
  
#### Parámetros  
 `pRetVal`  
 \[out\]  Devuelve `TRUE` si el segmento se puede escribir; de lo contrario, devuelve `FALSE`.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`.  devuelve `S_FALSE` si esta propiedad no se admite.  De lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)