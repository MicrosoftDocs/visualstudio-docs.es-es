---
title: "SetThreadCount | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "SetThreadCount"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "SetThreadCount"
ms.assetid: 335335a5-8ca0-4e18-95f5-62aa6a691386
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# SetThreadCount
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Establece el número de subprocesos global y lo asigna al subproceso actual.  
  
## Sintaxis  
  
```  
HRESULT WINAPI SetThreadCount(int threadCount);  
```  
  
#### Parámetros  
 \[in\] `threadCount`  
 El número de subprocesos que hay que utilizar.  
  
## Valor devuelto  
 Un [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True) con el bit [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True) establecido si se actualizó el número de subprocesos.  
  
## Requisitos  
 **Encabezado:** FileTracker.h