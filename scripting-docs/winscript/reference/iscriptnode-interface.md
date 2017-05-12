---
title: "IScriptNode (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IScriptNode (interfaz)"
ms.assetid: cfa76c4a-6543-48e8-a946-d212cd0bf934
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# IScriptNode (Interfaz)
Un objeto que implementa la interfaz de `IScriptNode` representa una página Web.  
  
 Además de los métodos heredados de `IUnknown`, la interfaz `IScriptNode` expone los métodos siguientes.  
  
## métodos en el orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md)|Indica si un objeto todavía está activa.|  
|[IScriptNode:: CreateChildEntry](../../winscript/reference/iscriptnode-createchildentry.md)|Agrega una instancia secundaria de `IScriptEntry`.|  
|[IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md)|Agrega un scriptlet como instancia secundaria de `IScriptNode`.|  
|[IScriptNode::Delete](../../winscript/reference/iscriptnode-delete.md)|Elimina el árbol de objetos.|  
|[IScriptNode::GetChild](../../winscript/reference/iscriptnode-getchild.md)|Devuelve el elemento secundario que está en el índice especificado en el nodo.|  
|[IScriptNode::GetCookie](../../winscript/reference/iscriptnode-getcookie.md)|Devuelve un valor definido por la aplicación que se utiliza para asociar un scriptlet con el objeto host.|  
|[IScriptNode::GetIndexInParent](../../winscript/reference/iscriptnode-getindexinparent.md)|Devuelve el índice de un objeto de la lista de elementos secundarios del elemento primario.|  
|[IScriptNode::GetLanguage](../../winscript/reference/iscriptnode-getlanguage.md)|Devuelve el lenguaje de comandos que usa el nodo actual del script.|  
|[IScriptNode::GetNumberOfChildren](../../winscript/reference/iscriptnode-getnumberofchildren.md)|Devuelve el número de nodos secundarios del objeto de `IScriptNode` .|  
|[IScriptNode::GetParent](../../winscript/reference/iscriptnode-getparent.md)|Devuelve el objeto de `IScriptNode` que es el elemento primario de un objeto.|  
  
## Vea también  
 [Active Script Authoring \(Interfaces\)](../../winscript/reference/active-script-authoring-interfaces.md)