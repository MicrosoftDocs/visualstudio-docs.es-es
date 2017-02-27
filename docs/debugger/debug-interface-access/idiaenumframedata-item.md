---
title: "IDiaEnumFrameData::Item | Microsoft Docs"
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
  - "IDiaEnumFrameData::Item (método)"
ms.assetid: 2761a72d-1868-4f5b-a32e-c2a1d9358c91
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumFrameData::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera un elemento de datos de cuadro mediante un índice.  
  
## Sintaxis  
  
```cpp#  
HRESULT Item (   
   DWORD           index,  
   IDiaFrameData** section  
);  
```  
  
#### Parámetros  
 índice  
 \[in\]  Índice del objeto de [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) que se recuperará.  El índice está en el intervalo de 0 a `count`\-1, donde `count` es devuelto por el método de [IDiaEnumFrameData::get\_Count](../../debugger/debug-interface-access/idiaenumframedata-get-count.md) .  
  
 sección  
 \[out\]  Devuelve un objeto de [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) que representa el elemento de datos deseado del cuadro.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)