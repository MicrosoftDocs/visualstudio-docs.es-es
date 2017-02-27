---
title: "IDiaStackFrame::get_lengthSavedRegisters | Microsoft Docs"
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
  - "IDiaStackFrame::get_lengthSavedRegisters (método)"
ms.assetid: b75fad6e-1ef4-44e6-89e3-c31c6fba10b3
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaStackFrame::get_lengthSavedRegisters
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

recupera el número de bytes de registros guardados insertados en la pila.  
  
## Sintaxis  
  
```cpp#  
HRESULT get_lengthSavedRegisters (   
   DWORD* pRetVal  
);  
```  
  
#### Parámetros  
 `pRetVal`  
 \[out\]  devuelve el número de bytes de registros guardados.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`.  Devuelve `S_FALSE` si no se admite.  De lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)