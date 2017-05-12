---
title: "IDebugApplicationNodeEvents::onAttach | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplicationNodeEvents.onAttach
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugApplicationNodeEvents::onAttach"
ms.assetid: b610c7e4-1c96-47ee-958e-3a1f5f621af3
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationNodeEvents::onAttach
Controla un evento indican que el objeto de nodo de aplicación de depuración se asocia a un nodo primario.  
  
## Sintaxis  
  
```  
HRESULT onAttach(  
   IDebugApplicationNode*  prddpParent  
);  
```  
  
#### Parámetros  
 `prddpParent`  
 \[in\] nodo de aplicación de depuración de El que es el elemento primario de este nodo.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método controla un evento indican que el objeto de nodo de aplicación de depuración se asocia a un nodo primario.  
  
 Los implementadores de la interfaz de `IDebugApplicationNode` provocan este evento.  
  
## Vea también  
 [IDebugApplicationNodeEvents \(Interfaz\)](../../winscript/reference/idebugapplicationnodeevents-interface.md)   
 [IDebugApplicationNodeEvents::onDetach](../../winscript/reference/idebugapplicationnodeevents-ondetach.md)   
 [IDebugApplicationNode \(Interfaz\)](../../winscript/reference/idebugapplicationnode-interface.md)