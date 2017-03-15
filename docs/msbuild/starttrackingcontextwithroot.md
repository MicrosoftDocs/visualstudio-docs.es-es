---
title: "StartTrackingContextWithRoot | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "StartTrackingContextWithRoot"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "StartTrackingContextWithRoot"
ms.assetid: f6ef2b76-8035-4a14-8195-aa221c46ef48
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# StartTrackingContextWithRoot
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Inicia un contexto de seguimiento mediante un archivo de respuesta que especifica un marcador raíz.  
  
## Sintaxis  
  
```  
HRESULT WINAPI StartTrackingContextWithRoot(LPCTSTR intermediateDirectory, LPCTSTR taskName, LPCTSTR rootMarkerResponseFile);  
```  
  
#### Parámetros  
 \[in\] `intermediateDirectory`  
 El directorio en el que se almacena el registro de seguimiento.  
  
 \[in\] `taskName`  
 Identifica el contexto de seguimiento.  Este nombre se utiliza para crear el nombre del archivo de registro.  
  
 \[in\] `rootMarkerResponseFile`  
 El nombre de ruta de acceso de un archivo de respuesta que contiene un marcador raíz.  El nombre raíz se utiliza para agrupar todo el seguimiento de un contexto.  
  
## Valor devuelto  
 Un [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True) con el bit [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True) establecido si se creó el contexto de seguimiento.  
  
## Requisitos  
 **Encabezado:** FileTracker.h  
  
## Vea también  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)