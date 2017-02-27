---
title: "IDiaSectionContrib::get_nopad | Microsoft Docs"
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
  - "IDiaSectionContrib::get_nopad (método)"
ms.assetid: f5c08603-0b3e-4e81-acf1-1b95a6a83bed
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IDiaSectionContrib::get_nopad
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera una marca que indica si la sección no se debe completar el límite siguiente de memoria.  
  
## Sintaxis  
  
```cpp#  
HRESULT get_nopad(  
   BOOL* pRetVal  
};  
```  
  
#### Parámetros  
 `pRetVal`  
 \[out\]  Devuelve `TRUE` si la sección se completa el límite siguiente de memoria; si no devuelve `FALSE`.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`.  devuelve `S_FALSE` si esta propiedad no se admite.  De lo contrario, devuelve un código de error.  
  
## Comentarios  
 Ésta es una propiedad consultada normalmente sólo en más archivos anteriores.  
  
## Vea también  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)