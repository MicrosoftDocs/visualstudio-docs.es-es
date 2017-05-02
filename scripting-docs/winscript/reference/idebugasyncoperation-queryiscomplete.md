---
title: "IDebugAsyncOperation::QueryIsComplete | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugAsyncOperation.QueryIsComplete
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugAsyncOperation::QueryIsComplete"
ms.assetid: fcf6e229-4d40-46d9-ab81-d3561bc8e084
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugAsyncOperation::QueryIsComplete
Determina si la operación de depuración ha finalizado.  
  
## Sintaxis  
  
```  
HRESULT QueryIsComplete();  
```  
  
#### Parámetros  
 Este método no toma ningún parámetro.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|Se completa la operación.|  
|`S_FALSE`|La operación no se completa.|  
  
## Comentarios  
 Este método determina si la operación de depuración ha finalizado.  
  
## Vea también  
 [IDebugAsyncOperation \(Interfaz\)](../../winscript/reference/idebugasyncoperation-interface.md)