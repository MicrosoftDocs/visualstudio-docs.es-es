---
title: "IDiaSymbol::get_unmodifiedTypeId | Microsoft Docs"
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
ms.assetid: 4f7fc73c-f524-4d7a-b378-a9ab99a96104
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::get_unmodifiedTypeId
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera el id. de original \(sin modificar\) con tipo.  
  
## Sintaxis  
  
```cpp  
HRESULT get_unmodifiedTypeId(   
   DWORD* pRetVal);  
```  
  
#### Parámetros  
 `pRetVal`  
 \[out\] puntero A `DWORD` que contiene el identificador  
  
## Valor devuelto  
 Si es correcto, especificado `S_OK`; si no, especificado `S_FALSE` o un código de error.  
  
## Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)