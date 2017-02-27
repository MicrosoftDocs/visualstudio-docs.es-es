---
title: "IDiaEnumLineNumbers::Skip | Microsoft Docs"
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
  - "IDiaEnumLineNumbers::Skip (método)"
ms.assetid: d182c269-8c76-4d8b-8275-c6807c5ae4e1
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumLineNumbers::Skip
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Omite un número especificado de números de línea en una secuencia de enumeración.  
  
## Sintaxis  
  
```cpp#  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### Parámetros  
 celt  
 \[in\]  El número de números de línea en la secuencia de enumeración al salto.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve `S_FALSE` si no hay números de línea a omitir.  
  
## Vea también  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)