---
title: "IDebugApplicationNode (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationNode (interfaz)"
ms.assetid: 30be3a97-8191-45ac-8706-3f7056c163d6
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugApplicationNode (Interfaz)
La interfaz de `IDebugApplicationNode` extiende la funcionalidad de la interfaz de `IDebugDocumentProvider` proporcionando un contexto dentro de un árbol de proyecto.  
  
 Además de los métodos heredados de `IDebugDocumentProvider`, la interfaz `IDebugApplicationNode` expone los métodos siguientes.  
  
## métodos en el orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugApplicationNode::EnumChildren](../../winscript/reference/idebugapplicationnode-enumchildren.md)|Enumera los nodos secundarios de este nodo de la aplicación.|  
|[IDebugApplicationNode::GetParent](../../winscript/reference/idebugapplicationnode-getparent.md)|Devuelve el nodo primario de este nodo de la aplicación.|  
|[IDebugApplicationNode::SetDocumentProvider](../../winscript/reference/idebugapplicationnode-setdocumentprovider.md)|Establece el proveedor del documento para este nodo de la aplicación.|  
|[IDebugApplicationNode::Close](../../winscript/reference/idebugapplicationnode-close.md)|Provoca esta aplicación para liberar todas las referencias y para entrar en un estado inactivo.|  
|[IDebugApplicationNode::Attach](../../winscript/reference/idebugapplicationnode-attach.md)|Agrega este nodo de la aplicación al árbol especificado del proyecto.|  
|[IDebugApplicationNode::Detach](../../winscript/reference/idebugapplicationnode-detach.md)|Quita este nodo de aplicación del árbol del proyecto.|