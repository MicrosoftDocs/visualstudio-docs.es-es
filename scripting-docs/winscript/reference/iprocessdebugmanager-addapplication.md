---
title: "IProcessDebugManager::AddApplication | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IProcessDebugManager.AddApplication
apilocation: pdm.dll
helpviewer_keywords: 
  - "IProcessDebugManager::AddApplication"
ms.assetid: 73828299-11eb-4c58-ad70-f80f2d0eede8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IProcessDebugManager::AddApplication
Agrega una aplicación a la lista de administrador de depuración de las aplicaciones en ejecución.  
  
## Sintaxis  
  
```  
HRESULT AddApplication(  
   IDebugApplication*  pda,  
   DWORD*              pdwAppCookie  
);  
```  
  
#### Parámetros  
 `pda`  
 \[in\] aplicación de depuración de El para agregar a la lista de aplicaciones en ejecución.  
  
 `pdwAppCookie`  
 \[out\] cookie de que se utiliza para quitar la aplicación de administrador de depuración de equipo.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método agrega una aplicación a la aplicación actual mostrada en el administrador de depuración de equipo.  
  
## Vea también  
 [IProcessDebugManager \(Interfaz\)](../../winscript/reference/iprocessdebugmanager-interface.md)   
 [IProcessDebugManager::RemoveApplication](../../winscript/reference/iprocessdebugmanager-removeapplication.md)