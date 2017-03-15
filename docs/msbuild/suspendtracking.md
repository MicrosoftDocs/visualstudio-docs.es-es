---
title: "SuspendTracking | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "SuspendTracking"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "SuspendTracking"
ms.assetid: f5e06e5a-8083-444c-99c1-07ba834226b5
caps.latest.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 3
---
# SuspendTracking
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Suspende el seguimiento en el contexto actual.  
  
## Sintaxis  
  
```  
HRESULT WINAPI SuspendTracking(void);  
```  
  
## Valor devuelto  
 Un [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True) con el bit [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True) establecido si se suspendió el seguimiento.  
  
## Requisitos  
 **Encabezado:** FileTracker.h  
  
## Vea también  
 [ResumeTracking](../msbuild/resumetracking.md)