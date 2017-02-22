---
title: "ResumeTracking | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "ResumeTracking"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "ResumeTracking"
ms.assetid: d637e019-7c50-4b0a-812e-bc822001e697
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# ResumeTracking
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Reanuda el seguimiento en el contexto actual.  
  
## Sintaxis  
  
```  
HRESULT WINAPI ResumeTracking();  
```  
  
## Valor devuelto  
 Un [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True) con el bit [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True) establecido si se reanudó el seguimiento.  [E\_FAIL](assetId:///E_FAIL?qualifyHint=False&autoUpgrade=True) se devuelve si no se puede reanudar el seguimiento porque el contexto no estaba disponible.  
  
## Requisitos  
 **Encabezado:** FileTracker.h  
  
## Vea también  
 [SuspendTracking](../msbuild/suspendtracking.md)