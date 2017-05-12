---
title: "IDebugApplicationNodeEvents::onRemoveChild | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplicationNodeEvents.onRemoveChild
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugApplicationNodeEvents::onRemoveChild"
ms.assetid: 2e025d29-b8c0-4793-a2d3-c20d548d6386
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationNodeEvents::onRemoveChild
Controla el evento cuando un nodo secundario se quita de un objeto de nodo de aplicación de depuración.  
  
## Sintaxis  
  
```  
HRESULT onRemoveChild(  
   IDebugApplicationNode*  prddpChild  
);  
```  
  
#### Parámetros  
 `prddpChild`  
 \[in\] nodo secundario de la aplicación a El que se quitó.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método controla el evento cuando un nodo secundario se quita de un objeto de nodo de aplicación de depuración.  
  
 Los implementadores de la interfaz de `IDebugApplicationNode` provocan este evento.  
  
## Vea también  
 [IDebugApplicationNodeEvents \(Interfaz\)](../../winscript/reference/idebugapplicationnodeevents-interface.md)   
 [IDebugApplicationNodeEvents::onAddChild](../../winscript/reference/idebugapplicationnodeevents-onaddchild.md)   
 [IDebugApplicationNode \(Interfaz\)](../../winscript/reference/idebugapplicationnode-interface.md)