---
title: "IScriptNode::Delete | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode.Delete
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::Delete"
ms.assetid: 6765ff80-a9a8-40a3-a669-7fcc284c87af
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptNode::Delete
Elimina este árbol de objetos.  
  
## Sintaxis  
  
```  
HRESULT Delete();  
```  
  
#### Parámetros  
 El método no toma ningún parámetro.  
  
## Valor devuelto  
 Interfaz `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Después de llamar al método de `Delete` , el método de [IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md) debe indicar que el nodo del script no está activo.  
  
## Vea también  
 [IScriptNode \(Interfaz\)](../../winscript/reference/iscriptnode-interface.md)