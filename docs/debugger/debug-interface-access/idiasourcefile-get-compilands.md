---
title: "IDiaSourceFile::get_compilands | Microsoft Docs"
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
  - "IDiaSourceFile::get_compilands (método)"
ms.assetid: 57deb50a-9c22-43ea-a80c-eab205997bc4
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSourceFile::get_compilands
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera un enumerador de los elementos que tienen números de línea que hacen referencia a este archivo.  
  
## Sintaxis  
  
```cpp#  
HRESULT get_compilands (   
   IDiaEnumSymbols** ppRetVal  
);  
```  
  
#### Parámetros  
 `ppRetVal`  
 \[out\]  Devuelve un objeto de [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) que contiene una lista de todos los elementos que tienen números de línea que hacen referencia a este archivo.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)