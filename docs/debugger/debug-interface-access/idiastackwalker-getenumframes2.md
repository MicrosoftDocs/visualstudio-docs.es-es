---
title: "IDiaStackWalker::getEnumFrames2 | Microsoft Docs"
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
  - "IDiaStackWalker2::getEnumFrames2 (método)"
ms.assetid: 73196d3f-112c-4b3a-997b-7c6b815d4afc
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IDiaStackWalker::getEnumFrames2
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera un enumerador del marco de pila para un tipo específico de plataforma.  
  
## Sintaxis  
  
```cpp#  
  
      HRESULT getEnumFrames2(   
   enum  CV_CPU_TYPE_e    cpuid,  
   IDiaStackWalkHelper*   pHelper,  
   IDiaEnumStackFrames**  ppEnum  
);  
```  
  
#### Parámetros  
 `cpuid`  
 \[in\]  Un valor de enumeración de [CV\_CPU\_TYPE\_e \(Enumeración\)](../../debugger/debug-interface-access/cv-cpu-type-e.md) , especificando el tipo de plataforma.  
  
 `pHelper`  
 \[in\]  El objeto de [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) auxiliares.  
  
 `ppEnum`  
 \[out\]  devuelve un objeto de [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md) que contiene una lista de objetos de [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) .  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Para obtener un marco de pila enumerado sólo para la plataforma x86, llame al método de [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) .  
  
## Vea también  
 [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)   
 [CV\_CPU\_TYPE\_e \(Enumeración\)](../../debugger/debug-interface-access/cv-cpu-type-e.md)   
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)