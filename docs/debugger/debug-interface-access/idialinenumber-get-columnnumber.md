---
title: "IDiaLineNumber::get_columnNumber | Microsoft Docs"
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
  - "IDiaLineNumber::get_columnNumber (método)"
ms.assetid: e317f29a-6525-46a7-8421-33985392f8fd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaLineNumber::get_columnNumber
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera el número de columnas en el que comienza la expresión o instrucción.  
  
## Sintaxis  
  
```  
[C++]  
HRESULT get_columnNumber (   
   DWORD* pRetVal  
);  
```  
  
#### Parámetros  
 `pRetVal`  
 \[out\]  Devuelve el número de columnas en el que comienza la expresión o instrucción.  Si el valor es cero, la información de la columna no está presente.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`.  devuelve `S_FALSE` si esta propiedad no se admite.  De lo contrario, devuelve un código de error.  
  
## Comentarios  
 El valor de la columna devuelto por este método es un desplazamiento de bytes en línea al primer carácter de la instrucción en la línea.  
  
## Vea también  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)