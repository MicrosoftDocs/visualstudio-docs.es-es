---
title: "IDiaEnumTables::Next | Microsoft Docs"
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
  - "IDiaEnumTables::Next (método)"
ms.assetid: 8d7bd359-d33e-4317-9674-d89283efd7de
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaEnumTables::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

recupera un número especificado de tablas en la secuencia de la enumeración.  
  
## Sintaxis  
  
```cpp#  
HRESULT Next (   
   ULONG       celt,  
   IDiaTable** rgelt,  
   ULONG*      pceltFetched  
);  
```  
  
#### Parámetros  
 `celt`  
 \[in\]  El número de tablas del enumerador que se recuperará.  
  
 `rgelt`  
 \[out\]  Una matriz que debe ser completo con objetos de [IDiaTable](../../debugger/debug-interface-access/idiatable.md) que representan las tablas deseadas.  
  
 `pceltFetched`  
 \[out\]  devuelve el número de tablas en el enumerador capturado.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`.  devuelve `S_FALSE` si no hay tablas.  De lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)