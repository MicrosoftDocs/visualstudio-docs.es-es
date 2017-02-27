---
title: "IDiaSymbol::get_isPointerToDataMember | Microsoft Docs"
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
ms.assetid: ef17c737-242e-43e8-b7e1-2c3bc58cfcef
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::get_isPointerToDataMember
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Especifica si este símbolo es un puntero a un miembro de datos.  
  
## Sintaxis  
  
```cpp  
HRESULT get_isPointerToDataMember(   
   BOOL* pRetVal);  
```  
  
#### Parámetros  
 `pRetVal`  
 \[out\] puntero A `BOOL` que especifica si este símbolo es un puntero a un miembro de datos.  
  
## Valor devuelto  
 Si es correcto, especificado `S_OK`; si no, especificado `S_FALSE` o un código de error.  
  
## Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)