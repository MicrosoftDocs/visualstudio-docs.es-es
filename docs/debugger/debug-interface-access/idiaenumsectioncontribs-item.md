---
title: "IDiaEnumSectionContribs::Item | Microsoft Docs"
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
  - "IDiaEnumSectionContribs::Item (método)"
ms.assetid: 63a28f23-0ca0-44a7-b11b-ca0206d642a0
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumSectionContribs::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

recupera contribuciones de la sección mediante un índice.  
  
## Sintaxis  
  
```cpp#  
HRESULT Item (   
   DWORD                index,  
   IDiaSectionContrib** section  
);  
```  
  
#### Parámetros  
 índice  
 \[in\]  Índice del objeto de [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) que se recuperará.  El índice está en el intervalo de 0 a `count`\-1, donde `count` es devuelto por el método de [IDiaEnumSectionContribs::get\_Count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md) .  
  
 sección  
 \[out\]  devuelve un objeto de [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) que representa la contribución deseada de la sección.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDiaEnumSectionContribs::get\_Count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md)   
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)