---
title: "IMachineDebugManagerCookie::AddApplication | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IMachineDebugManagerCookie.AddApplication
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IMachineDebugManagerCookie::AddApplication"
ms.assetid: 4d5503c5-aca9-4cf7-9900-f77bf5f3263d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IMachineDebugManagerCookie::AddApplication
Agrega una aplicación a la lista actual de la aplicación.  
  
## Sintaxis  
  
```  
HRESULT AddApplication(  
   IRemoteDebugApplication*  pda,  
   DWORD                     dwDebugAppCookie,  
   DWORD*                    pdwAppCookie  
);  
```  
  
#### Parámetros  
 `pda`  
 \[in\] aplicación a la lista actual de la aplicación.  
  
 `dwDebugAppCookie`  
 \[in\] cookie de que identifica la aplicación de depuración.  
  
 `pdwAppCookie`  
 \[out\] cookie de que se utiliza para quitar la aplicación de administrador de depuración de equipo.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método llama el administrador de la depuración siempre que se llame a `IProcessDebugManager::AddApplication` .  
  
## Vea también  
 [IMachineDebugManagerCookie \(Interfaz\)](../../winscript/reference/imachinedebugmanagercookie-interface.md)   
 [IMachineDebugManagerCookie::RemoveApplication](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)   
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)