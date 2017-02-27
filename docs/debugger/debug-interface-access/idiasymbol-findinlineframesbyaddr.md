---
title: "IDiaSymbol::findInlineFramesByAddr | Microsoft Docs"
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
ms.assetid: 36a122e6-f27e-40cd-9784-cdaf279e1905
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::findInlineFramesByAddr
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera una enumeración que permite que un cliente recorrer en iteración todos los marcos de punto flotante en una dirección especificada.  
  
## Sintaxis  
  
```cpp#  
HRESULT findInlineFramesByAddr (   
   DWORD             isect,  
   DWORD             offset,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### Parámetros  
 `isect`  
 \[in\] especifica el componente de la sección de dirección.  
  
 `offset`  
 \[in\] especifica el componente de desplazamiento de dirección.  
  
 `ppResult`  
 \[out\] contiene un objeto de `IDiaEnumSymbols` que contiene la lista de marcos se recuperen que.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum \(Enumeración\)](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)