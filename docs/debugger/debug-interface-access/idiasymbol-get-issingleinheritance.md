---
title: "IDiaSymbol::get_isSingleInheritance | Microsoft Docs"
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
ms.assetid: 46cde656-059b-4c20-9476-3ca68ccc9912
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::get_isSingleInheritance
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Especifica si los puntos del puntero de `this` un miembro de datos con herencia única.  
  
## Sintaxis  
  
```cpp  
HRESULT get_isSingleInheritance(   
   BOOL* pRetVal);  
```  
  
#### Parámetros  
 `pRetVal`  
 \[out\] puntero A `BOOL` que especifica si el puntero de `this` señala a un miembro de datos con herencia única.  
  
## Valor devuelto  
 Si es correcto, especificado `S_OK`; si no, especificado `S_FALSE` o un código de error.  
  
## Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)