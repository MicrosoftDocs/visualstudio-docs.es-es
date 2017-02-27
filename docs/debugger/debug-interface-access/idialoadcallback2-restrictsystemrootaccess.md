---
title: "IDiaLoadCallback2::RestrictSystemRootAccess | Microsoft Docs"
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
  - "IDiaLoadCallback2::RestrictSystemRootAccess (método)"
ms.assetid: 39f22db8-632a-4ef0-babc-23f758e6d937
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaLoadCallback2::RestrictSystemRootAccess
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Determina si el buscar archivos .pdb se permite en el directorio raíz del sistema.  
  
## Sintaxis  
  
```cpp#  
HRESULT RestrictSystemRootAccess();  
```  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Cualquier código devuelto distinto de `S_OK` evita buscar la raíz del sistema para los archivos .pdb.  
  
## Vea también  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)