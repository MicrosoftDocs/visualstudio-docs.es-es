---
title: "IDebugApplicationNode::EnumChildren | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplicationNode.EnumChildren
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplicationNode::EnumChildren"
ms.assetid: d79b362b-23d5-4a5e-a214-5a78618eaf71
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationNode::EnumChildren
Enumera los nodos secundarios de este nodo de la aplicación.  
  
## Sintaxis  
  
```  
HRESULT EnumChildren(  
   IEnumDebugApplicationNodes**  pperddp  
);  
```  
  
#### Parámetros  
 `pperddp`  
 \[out\] enumeración de los nodos secundarios de este nodo.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método enumera los nodos secundarios de este nodo de la aplicación.  
  
## Vea también  
 [IDebugApplicationNode \(Interfaz\)](../../winscript/reference/idebugapplicationnode-interface.md)