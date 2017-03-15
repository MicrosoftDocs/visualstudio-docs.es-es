---
title: "IDiaLoadCallback2::RestrictReferencePathAccess | Microsoft Docs"
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
  - "IDiaLoadCallback2::RestrictReferencePathAccess (método)"
ms.assetid: e20cb45c-0360-4ff0-a92c-b1b6f76d6e85
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaLoadCallback2::RestrictReferencePathAccess
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Determina si se buscan un archivo .pdb se permite en la ruta de acceso donde se encuentra el archivo .exe.  
  
## Sintaxis  
  
```cpp#  
HRESULT RestrictReferencePathAccess();  
```  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Cualquier código devuelto distinto de `S_OK` para evitar buscar un archivo .pdb en la ruta de acceso donde se encuentra el archivo .exe.  
  
## Vea también  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)