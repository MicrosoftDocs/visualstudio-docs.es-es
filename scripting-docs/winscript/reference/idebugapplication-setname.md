---
title: "IDebugApplication::SetName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.SetName
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::SetName"
ms.assetid: 7b0ddc58-6f20-4ce3-9bdf-81a6c1d64256
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::SetName
Establece el nombre de la aplicación.  
  
## Sintaxis  
  
```  
HRESULT SetName(  
   LPCOLESTR  pstrName  
);  
```  
  
#### Parámetros  
 `pstrName`  
 \[in\] Nombre de la aplicación.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 El nombre proporcionado a este método se devuelve en llamadas subsiguientes al método de `IRemoteDebugApplication::GetName` .  
  
 Se debe llamar a este método antes de llamar al método de `IProcessDebugManager::AddApplication` .  
  
## Vea también  
 [IDebugApplication \(Interfaz\)](../../winscript/reference/idebugapplication-interface.md)   
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)