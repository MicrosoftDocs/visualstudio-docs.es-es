---
title: "IDiaEnumSectionContribs::Next | Microsoft Docs"
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
  - "IDiaEnumSectionContribs::Next (método)"
ms.assetid: a6bb2adb-ee6d-4f3c-ab5b-e89361c8880e
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumSectionContribs::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera un número especificado de contribuciones de la sección de la secuencia de la enumeración.  
  
## Sintaxis  
  
```cpp#  
HRESULT Next(   
   ULONG                celt,   
   IDiaSectionContrib** rgelt,  
   ULONG*               pceltFetched  
);  
```  
  
#### Parámetros  
 celt  
 \[in\]  El número de contribuciones de la sección del enumerador que se recuperará.  
  
 rgelt  
 \[out\]  Una matriz que debe rellenarse con los objetos de [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) que representan las contribuciones deseadas de la sección.  
  
 pceltFetched  
 \[out\]  Devuelve el número de contribuciones de la sección del enumerador capturado.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`.  devuelve `S_FALSE` si no hay contribuciones de la sección.  De lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)   
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)