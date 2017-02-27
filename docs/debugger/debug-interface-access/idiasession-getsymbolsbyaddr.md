---
title: "IDiaSession::getSymbolsByAddr | Microsoft Docs"
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
  - "IDiaSession::getSymbolsByAddr (método)"
ms.assetid: eafcc757-b488-487d-a063-ad3703ff42e8
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSession::getSymbolsByAddr
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera un enumerador que encuentra símbolos en el orden de las direcciones.  
  
## Sintaxis  
  
```cpp#  
HRESULT getSymbolsByAddr(   
   IDiaEnumSymbolsByAddr** ppEnumbyAddr  
);  
```  
  
#### Parámetros  
 `ppEnumbyAddr`  
 \[out\]  devuelve un objeto de [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md) .  Utilice esta interfaz para buscar símbolos en el token almacenado por la ubicación de memoria.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)