---
title: "IDiaSession::symsAreEquiv | Microsoft Docs"
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
  - "IDiaSession::symsAreEquiv (método)"
ms.assetid: 9941d520-e203-46c0-83c3-b3a967f4fc59
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSession::symsAreEquiv
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Comprueba si dos símbolos son equivalentes.  
  
## Sintaxis  
  
```cpp#  
HRESULT symsAreEquiv (   
   IDiaSymbol* symbolA,  
   IDiaSymbol* symbolB  
);  
```  
  
#### Parámetros  
 `symbolA`  
 \[in\]  el primer objeto de [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) utilizado en la comparación.  
  
 `symbolB`  
 \[in\]  el segundo objeto de `IDiaSymbol` utilizado en la comparación.  
  
## Valor devuelto  
 si los símbolos son equivalentes, devuelve `S_OK`; de lo contrario, devuelve `S_FALSE`, los símbolos no son equivalentes.  De lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)