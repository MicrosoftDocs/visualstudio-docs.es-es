---
title: "IDiaEnumSegments::Item | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaEnumSegments::Item (método)"
ms.assetid: ee44dd55-39a0-4b7b-97ff-2e1226eeb2bd
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumSegments::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

recupera un segmento mediante un índice.  
  
## Sintaxis  
  
```cpp#  
HRESULT Item (   
   DWORD         index,  
   IDiaSegment** segment  
);  
```  
  
#### Parámetros  
 índice  
 \[in\]  Índice del objeto de [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) que se recuperará.  El índice está en el intervalo de 0 a `count`\-1, donde `count` es devuelto por el método de [IDiaEnumSegments::get\_Count](../../debugger/debug-interface-access/idiaenumsegments-get-count.md) .  
  
 segmento  
 \[out\]  devuelve un objeto de [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) que representa el segmento deseado.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)