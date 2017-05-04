---
title: "IScriptNode::Alive | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode.Alive
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::Alive"
ms.assetid: d2755c83-e9b9-4c0a-acb7-25b554fc9fe8
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IScriptNode::Alive
Indica si un objeto todavía está activa.  
  
## Sintaxis  
  
```  
HRESULT Alive();  
```  
  
#### Parámetros  
 El método no toma ningún parámetro.  
  
## Valor devuelto  
 Interfaz `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El nodo de script todavía está activa.|  
  
## Comentarios  
 Si el objeto no está activo, el modelo de objetos componentes \(COM\) devuelve un error de proxy del cálculo de referencias de las llamadas a este método.  
  
## Vea también  
 [IScriptNode \(Interfaz\)](../../winscript/reference/iscriptnode-interface.md)