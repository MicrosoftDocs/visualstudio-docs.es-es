---
title: "IDebugApplicationNodeEvents (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationNodeEvents (interfaz)"
ms.assetid: 02e0bb17-84ce-458b-bae6-608a9899e535
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationNodeEvents (Interfaz)
Proporciona la interfaz de eventos de la interfaz de `IDebugApplicationNode` .  
  
 Además de los métodos heredados de `IUnknown`, la interfaz `IDebugApplicationNodeEvents` expone los métodos siguientes.  
  
## métodos en el orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugApplicationNodeEvents::onAddChild](../../winscript/reference/idebugapplicationnodeevents-onaddchild.md)|Controla el evento cuando un nodo secundario se agrega a un objeto de nodo de aplicación de depuración.|  
|[IDebugApplicationNodeEvents::onRemoveChild](../../winscript/reference/idebugapplicationnodeevents-onremovechild.md)|Controla el evento cuando un nodo secundario se quita de un objeto de nodo de aplicación de depuración.|  
|[IDebugApplicationNodeEvents::onDetach](../../winscript/reference/idebugapplicationnodeevents-ondetach.md)|Controla un evento indican que el objeto de nodo de aplicación de depuración se desasoció de un nodo primario.|  
|[IDebugApplicationNodeEvents::onAttach](../../winscript/reference/idebugapplicationnodeevents-onattach.md)|Controla un evento indican que el objeto de nodo de aplicación de depuración se asocia a un nodo primario.|  
  
## Vea también  
 [IDebugApplicationNode \(Interfaz\)](../../winscript/reference/idebugapplicationnode-interface.md)