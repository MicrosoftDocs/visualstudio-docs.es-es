---
title: "WriteAllTLogs | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "WriteAllTLogs"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "WriteAllTLogs"
ms.assetid: 1fa3e10b-263c-4960-a9ad-485c02a7a872
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# WriteAllTLogs
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Escribe registros de seguimiento para todos los contextos y subprocesos.  
  
## Sintaxis  
  
```  
HRESULT WINAPI WriteAllTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);  
```  
  
#### Parámetros  
 \[in\] `intermediateDirectory`  
 El directorio en el que se almacena el registro de seguimiento.  
  
 \[in\] `tlogRootName`  
 El nombre raíz del nombre del archivo de registro.  
  
## Valor devuelto  
 Un [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True) con el bit [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True) establecido si se creó el contexto de seguimiento.  
  
## Requisitos  
 **Encabezado:** FileTracker.h  
  
## Vea también  
 [WriteContextTLogs](../msbuild/writecontexttlogs.md)