---
title: "IDebugExpression::QueryIsComplete | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExpression.QueryIsComplete
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugExpression::QueryIsComplete"
ms.assetid: 510d62e5-a316-46fb-b23f-d3ba902b295c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpression::QueryIsComplete
Determina si se completa la operación.  
  
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
|`S_OK`|El método correcto, y la operación se completa.|  
|`S_FALSE`|La operación todavía está pendiente.|  
  
## Comentarios  
 Este método determina si se completa la operación.  
  
## Vea también  
 [IDebugExpression \(Interfaz\)](../../winscript/reference/idebugexpression-interface.md)