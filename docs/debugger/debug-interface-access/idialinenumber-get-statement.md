---
title: "IDiaLineNumber::get_statement | Microsoft Docs"
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
  - "IDiaLineNumber::get_statement (método)"
ms.assetid: 22b8ee29-79ef-427f-bd05-00d255ab836b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaLineNumber::get_statement
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera un mensaje que indica que esta información de línea describe el principio de una instrucción, en lugar de una expresión, en el origen del programa.  
  
## Sintaxis  
  
```cpp#  
HRESULT get_statement (   
   BOOL* pRetVal  
);  
```  
  
#### Parámetros  
 `pRetVal`  
 \[out\]  Devuelve `TRUE` si esta información de línea describe el principio de una instrucción en el origen del programa.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`.  devuelve `S_FALSE` si esta propiedad no se admite.  De lo contrario, devuelve un código de error.  
  
## Comentarios  
 Las instrucciones pueden abarcar varias líneas.  Este método indica si el número de línea asociado marca el principio de una instrucción en varias líneas.  
  
## Vea también  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)