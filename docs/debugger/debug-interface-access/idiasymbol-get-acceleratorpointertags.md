---
title: "IDiaSymbol::get_acceleratorPointerTags | Microsoft Docs"
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
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::get_acceleratorPointerTags
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Devuelve todos los valores de etiqueta de puntero de aceleradores que corresponden a la función de código auxiliar de aceleradores de AMP en cuestión.  
  
## Sintaxis  
  
```cpp  
HRESULT get_acceleratorPointerTags(   
   DWORD          cnt,  
   DWORD*         pcnt,  
   DWORD*         pPointerTags);  
```  
  
#### Parámetros  
 `cnt`  
 \[in\] tamaño del `pPointerTags`matriz de salida.  
  
 `pcnt`  
 \[out\] número de etiquetas de puntero de aceleradores en la función de código auxiliar de aceleradores de AMP de C\+\+.  
  
 `pPointerTags`  
 \[out\] puntero de matriz de A `DWORD` que se rellena con los valores de etiqueta de puntero de aceleradores en la función de código auxiliar de aceleradores de AMP de C\+\+.  
  
## Valor devuelto  
 Si es correcto, especificado `S_OK`; si no, especificado `S_FALSE` o un código de error.  
  
## Comentarios  
 Este método se llama una interfaz de `IDiaSymbol` que corresponda a la función de código auxiliar de aceleradores de AMP en cuestión.  
  
## Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)