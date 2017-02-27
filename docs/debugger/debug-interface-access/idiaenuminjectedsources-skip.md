---
title: "IDiaEnumInjectedSources::Skip | Microsoft Docs"
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
  - "IDiaEnumInjectedSources::Skip (método)"
ms.assetid: 4aad6a51-f2d3-4064-b216-60d830d0a560
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumInjectedSources::Skip
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Omite un número especificado de orígenes insertados en una secuencia de enumeración.  
  
## Sintaxis  
  
```cpp#  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### Parámetros  
 celt  
 \[in\]  El número de orígenes insertados en la secuencia de enumeración al salto.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve `S_FALSE` si no hay orígenes incrustados a omitir.  
  
## Vea también  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)