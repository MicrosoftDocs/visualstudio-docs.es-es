---
title: "IDiaEnumInjectedSources::Next | Microsoft Docs"
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
  - "IDiaEnumInjectedSources::Next (método)"
ms.assetid: 38af80fc-748f-4b15-bff1-823db21dd4d0
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumInjectedSources::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

recupera un número especificado de orígenes insertados en la secuencia de la enumeración.  
  
## Sintaxis  
  
```cpp#  
HRESULT Next (   
   ULONG                celt,   
   IDiaInjectedSource** rgelt,  
   ULONG*               pceltFetched  
);  
```  
  
#### Parámetros  
 celt  
 \[in\]  el número de orígenes insertados en el enumerador que se recuperará.  
  
 rgelt  
 \[out\]  Devuelve una matriz de los objetos de [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) que representa los orígenes insertados deseados.  
  
 pceltFetched  
 \[out\]  devuelve el número de orígenes insertados en el enumerador capturado.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`.  Devuelve `S_FALSE` si no hay orígenes incrustados.  De lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)   
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)