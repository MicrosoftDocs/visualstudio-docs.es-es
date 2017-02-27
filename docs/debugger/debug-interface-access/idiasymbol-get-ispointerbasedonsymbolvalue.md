---
title: "IDiaSymbol::get_isPointerBasedOnSymbolValue | Microsoft Docs"
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
ms.assetid: 577c8011-9269-4373-8577-b4822a983724
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::get_isPointerBasedOnSymbolValue
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Especifica si el puntero de `this` está basado en un valor de símbolo.  
  
## Sintaxis  
  
```cpp  
HRESULT get_isPointerBasedOnSymbolValue(   
   BOOL* pRetVal);  
```  
  
#### Parámetros  
 `pRetVal`  
 \[out\] puntero A `BOOL` que especifica si el puntero de `this` está basado en un valor de símbolo.  
  
## Valor devuelto  
 Si es correcto, especificado `S_OK`; si no, especificado `S_FALSE` o un código de error.  
  
## Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)