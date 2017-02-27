---
title: "IDiaEnumSourceFiles::Next | Microsoft Docs"
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
  - "IDiaEnumSourceFiles::Next (método)"
ms.assetid: 83bf6317-ff39-4c5c-8987-cba34e7a6983
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumSourceFiles::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera un número especificado de archivos de código fuente de la secuencia de la enumeración.  
  
## Sintaxis  
  
```cpp#  
HRESULT Next (   
   ULONG            celt,  
   IDiaSourceFile** rgelt,  
   ULONG*           pceltFetched  
);  
```  
  
#### Parámetros  
 celt  
 \[in\]  el número de archivos de código fuente en el enumerador que se recuperará.  
  
 rgelt  
 \[out\]Una matriz que debe ser completo con objetos de [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) que representan archivos de código fuente deseados.  
  
 pceltFetched  
 \[out\]  devuelve el número de archivos de código fuente en el enumerador capturado.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`.  devuelve `S_FALSE` si no hay archivos de código fuente.  De lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)   
 [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)