---
title: "IDiaEnumSymbolsByAddr::symbolByVA | Microsoft Docs"
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
  - "IDiaEnumSymbolsByAddr::symbolByVA (método)"
ms.assetid: ac84339f-70c6-48ed-85d0-6d7d1b5194e8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaEnumSymbolsByAddr::symbolByVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Coloca el enumerador mediante una búsqueda de la dirección virtual \(VA\).  
  
## Sintaxis  
  
```cpp#  
HRESULT symbolByVA (   
   DWORD**      virtualAddress,  
   IDiaSymbol** ppsymbol  
);  
```  
  
#### Parámetros  
 virtualAddress  
 \[in\]  dirección virtual.  
  
 ppsymbol  
 \[out\]  devuelve un objeto de [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) que representa el símbolo encontrado.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`.  Devuelve `S_FALSE` si el símbolo no se encuentra.  De lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)