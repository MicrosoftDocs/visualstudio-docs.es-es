---
title: "IDiaEnumSegments::Clone | Microsoft Docs"
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
  - "IDiaEnumSegments::Clone (método)"
ms.assetid: 93deaac6-72ab-4408-ba14-66174a618757
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumSegments::Clone
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Crea un enumerador que contiene al mismo estado de enumeración que el enumerador actual.  
  
## Sintaxis  
  
```cpp#  
HRESULT Clone (   
   IDiaEnumSegments** ppenum  
);  
```  
  
#### Parámetros  
 ppenum  
 \[out\]  Devuelve un objeto de [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md) que contiene un duplicado del enumerador.  Los segmentos no se duplican, sólo el enumerador.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)