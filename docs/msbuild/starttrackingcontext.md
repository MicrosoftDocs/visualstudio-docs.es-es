---
title: "StartTrackingContext | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "StartTrackingContext"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "StartTrackingContext"
ms.assetid: 720cd295-38e7-4974-86db-b8106b1207ba
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# StartTrackingContext
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Inicie un contexto de seguimiento.  
  
## Sintaxis  
  
```  
HRESULT WINAPI StartTrackingContext(LPCTSTR intermediateDirectory, LPCTSTR taskName);  
```  
  
#### Parámetros  
 \[in\] `intermediateDirectory`  
 El directorio en el que se almacena el registro de seguimiento.  
  
 \[in\] `taskName`  
 Identifica el contexto de seguimiento.  Este nombre se utiliza para crear el nombre del archivo de registro.  
  
## Valor devuelto  
 Un [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True) con el bit [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True) establecido si se creó el contexto de seguimiento.  
  
## Requisitos  
 **Encabezado:** FileTracker.h