---
title: "IProcessDebugManager (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IProcessDebugManager (interfaz)"
ms.assetid: b6ecb2bd-a4d1-4857-9232-036c154d0cb1
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IProcessDebugManager (Interfaz)
Interfaz principal al administrador de la depuración.  Esta interfaz puede crear, agregar, o quitar una aplicación virtual de un proceso.  Puede enumerar los marcos de pila y los subprocesos de la aplicación.  
  
 Además de los métodos heredados de `IUnknown`, la interfaz `IProcessDebugManager` expone los métodos siguientes.  
  
## métodos en el orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IProcessDebugManager::CreateApplication](../../winscript/reference/iprocessdebugmanager-createapplication.md)|Crea un nuevo objeto application de depuración para esta aplicación.|  
|[IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)|Devuelve un objeto de aplicación predeterminado para el proceso actual.|  
|[IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)|Agrega una aplicación a la lista de administrador de depuración de las aplicaciones en ejecución.|  
|[IProcessDebugManager::RemoveApplication](../../winscript/reference/iprocessdebugmanager-removeapplication.md)|Quita una aplicación de la lista actual de la aplicación.|  
|[IProcessDebugManager::CreateDebugDocumentHelper](../../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md)|Crea una nueva aplicación auxiliar de depuración para esta aplicación.|