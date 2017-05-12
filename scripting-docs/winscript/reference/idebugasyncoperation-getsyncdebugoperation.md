---
title: "IDebugAsyncOperation::GetSyncDebugOperation | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugAsyncOperation.GetSyncDebugOperation
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugAsyncOperation::GetSyncDebugOperation"
ms.assetid: ff89a3bc-57d7-4cb9-9818-8d73ed71af73
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugAsyncOperation::GetSyncDebugOperation
Devuelve la operación sincrónica de depuración asociada a este objeto.  
  
## Sintaxis  
  
```  
HRESULT GetSyncDebugOperation(  
   IDebugSyncOperation**  ppsdo  
);  
```  
  
#### Parámetros  
 `ppsdo`  
 \[out\] operación sincrónica de depuración se asociada a este objeto.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método devuelve la operación sincrónica de depuración asociada a este objeto.  
  
## Vea también  
 [IDebugAsyncOperation \(Interfaz\)](../../winscript/reference/idebugasyncoperation-interface.md)