---
title: "IDiaSymbol::get_builtInKind | Microsoft Docs"
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
ms.assetid: 953e6dba-582e-4b76-b736-898b92e5693e
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::get_builtInKind
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera una clase integrada del tipo de HLSL.  
  
## Sintaxis  
  
```cpp  
HRESULT get_buildInKind(   
   DWORD* pRetVal);  
```  
  
#### Parámetros  
 `pRetVal`  
 \[out\] puntero A `DWORD` que contiene una clase integrada del tipo de HLSL.  
  
## Valor devuelto  
 Si es correcto, especificado `S_OK`; si no, especificado `S_FALSE` o un código de error.  
  
## Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)