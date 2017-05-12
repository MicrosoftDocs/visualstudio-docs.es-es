---
title: "IScriptNode::GetParent | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode.GetParent
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::GetParent"
ms.assetid: 0fb813f6-ab94-46b2-b0cf-ef5d1cd38ae4
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IScriptNode::GetParent
Devuelve el objeto de `IScriptNode` que es el elemento primario de un objeto.  
  
## Sintaxis  
  
```  
HRESULT GetParent(  
   IScriptNode       **ppsnParent  
);  
```  
  
#### Parámetros  
 `ppsnParent`  
 \[out\] dirección de una variable que recibe un puntero a la interfaz de `IScriptNode` de la instancia primaria.  
  
 Si la clase implementa `IScriptEntry` o `IScriptScriptlet`, se devuelve un objeto de `IScriptNode` .  
  
 Si la clase implementa `IScriptNode`\(que representa una página Web\), se devuelve NULL.  
  
## Valor devuelto  
 Interfaz `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
  
## Vea también  
 [IScriptNode \(Interfaz\)](../../winscript/reference/iscriptnode-interface.md)