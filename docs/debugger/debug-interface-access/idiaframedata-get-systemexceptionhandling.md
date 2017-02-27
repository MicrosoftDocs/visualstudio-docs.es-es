---
title: "IDiaFrameData::get_systemExceptionHandling | Microsoft Docs"
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
  - "IDiaFrameData::get_systemExceptionHandling (método)"
ms.assetid: e8df1972-913c-446c-9779-775575b0caa9
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaFrameData::get_systemExceptionHandling
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera una marca que indica si el control de excepciones en el sistema está en vigor.  
  
## Sintaxis  
  
```cpp#  
HRESULT get_systemExceptionHandling (   
   BOOL* pRetVal  
);  
```  
  
#### Parámetros  
 pRetVal  
 \[out\]  Devuelve `TRUE` si el control de excepciones del sistema está vigente; de lo contrario, devuelve `FALSE`.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`.  devuelve `S_FALSE` si esta propiedad no se admite.  De lo contrario, devuelve un código de error.  
  
## Comentarios  
 El control de excepciones del sistema se conoce normalmente como control de excepciones estructurado.  
  
 Para determinar si el control de excepciones de C\+\+ está vigente, llame al método de [IDiaFrameData::get\_cplusplusExceptionHandling](../../debugger/debug-interface-access/idiaframedata-get-cplusplusexceptionhandling.md) .  
  
## Vea también  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get\_cplusplusExceptionHandling](../../debugger/debug-interface-access/idiaframedata-get-cplusplusexceptionhandling.md)