---
title: "IScriptNode::GetChild | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode.GetChild
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::GetChild"
ms.assetid: 8cb3f8b0-958b-40bb-a91a-49a788661861
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptNode::GetChild
Devuelve el elemento secundario que está en el índice especificado en el nodo.  
  
## Sintaxis  
  
```  
HRESULT GetChild(  
   ULONG              isn,  
   IScriptNode        **ppsn  
);  
```  
  
#### Parámetros  
 `isn`  
 \[in\] índice del elemento secundario del elemento primario.  
  
 `ppsn`  
 \[out\] dirección de una variable que recibe un puntero a la interfaz de `IScriptNode` de instancia secundaria.  
  
 Para los objetos de `IScriptNode` que representan una página Web, retornos de este parámetro un objeto que contiene un bloque de script.  
  
 Para los objetos de `IScriptEntry` que especifican un bloque script, retornos de este parámetro un objeto que especifica una función.  
  
## Valor devuelto  
 Interfaz `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Para los objetos de `IScriptEntry` que especifican un objeto de función y para los objetos de `IScriptScriptlet` , error en este método porque no hay entradas secundarias.  
  
## Vea también  
 [IScriptNode \(Interfaz\)](../../winscript/reference/iscriptnode-interface.md)