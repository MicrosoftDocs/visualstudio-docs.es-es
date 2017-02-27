---
title: "IDiaSegment::get_offset | Microsoft Docs"
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
  - "IDiaSegment::get_offset (método)"
ms.assetid: 97415ac6-b072-4e3c-9dd3-73087ae605fc
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSegment::get_offset
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera el desplazamiento, en segmentos, donde comienza la sección.  
  
## Sintaxis  
  
```cpp#  
HRESULT get_offset (   
   DWORD* pRetVal  
);  
```  
  
#### Parámetros  
 `pRetVal`  
 \[out\]  Devuelve la diferencia, en segmentos, donde comienza la sección.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`.  devuelve `S_FALSE` si esta propiedad no se admite.  De lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)