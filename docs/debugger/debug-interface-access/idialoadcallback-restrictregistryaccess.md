---
title: "IDiaLoadCallback::RestrictRegistryAccess | Microsoft Docs"
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
  - "IDiaLoadCallback::RestrictRegistryAccess (método)"
ms.assetid: de4760c3-a746-4bab-8065-1388fed31b67
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaLoadCallback::RestrictRegistryAccess
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Determina si las consultas del registro pueden usarse para localizar las rutas de búsqueda de símbolos.  
  
## Sintaxis  
  
```cpp#  
HRESULT RestrictRegistryAccess();  
```  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Cualquier código devuelto distinto de `S_OK` impide ver el registro de las rutas de búsqueda de símbolos.  
  
## Vea también  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)