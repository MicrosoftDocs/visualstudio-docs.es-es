---
title: "IDiaEnumSectionContribs::Skip | Microsoft Docs"
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
  - "IDiaEnumSectionContribs::Skip (método)"
ms.assetid: 7471a178-5134-41b2-80a6-51ff96abe916
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaEnumSectionContribs::Skip
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Omite un número especificado de contribuciones de la sección en una secuencia de enumeración.  
  
## Sintaxis  
  
```cpp#  
HRESULT Skip(   
   ULONG celt  
);  
```  
  
#### Parámetros  
 `celt`  
 \[in\]  El número de contribuciones de sección en la secuencia de enumeración al salto.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve `S_FALSE` si no hay contribuciones de sección a omitir.  
  
## Vea también  
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)