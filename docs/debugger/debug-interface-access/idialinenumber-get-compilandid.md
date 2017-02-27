---
title: "IDiaLineNumber::get_compilandId | Microsoft Docs"
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
  - "IDiaLineNumber::get_compilandId (método)"
ms.assetid: 2cd6f551-8091-47c7-803f-3f79a766a211
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaLineNumber::get_compilandId
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera un identificador único para la compilación que contribuyó esta línea.  
  
## Sintaxis  
  
```cpp#  
HRESULT get_compilandId (   
   DWORD* pRetVal  
);  
```  
  
#### Parámetros  
 `pRetVal`  
 \[out\]  Devuelve `DWORD` que contiene el identificador único para la compilación que contribuyó esta línea.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`.  devuelve `S_FALSE` si esta propiedad no se admite.  De lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)