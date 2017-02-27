---
title: "IDiaEnumTables::Clone | Microsoft Docs"
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
  - "IDiaEnumTables::Clone (método)"
ms.assetid: beb21109-b12c-44d8-8c1f-a332216b3713
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaEnumTables::Clone
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Crea un enumerador que contiene al mismo estado de enumeración que el enumerador actual.  
  
## Sintaxis  
  
```cpp#  
HRESULT Clone (   
   IDiaEnumTables** ppenum  
);  
```  
  
#### Parámetros  
 `ppenum`  
 \[out\]  Devuelve un objeto de [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md) que contiene un duplicado del enumerador.  Las tablas no se duplican, sólo el enumerador.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)