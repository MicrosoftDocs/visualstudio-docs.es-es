---
title: "IActiveScriptSiteDebug::GetApplication | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteDebug.GetApplication
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteDebug::GetApplication"
ms.assetid: 4400f1b1-3108-4a71-b1f1-43586fe1227c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteDebug::GetApplication
Devuelve el objeto application de depuración asociado a este sitio de script.  
  
## Sintaxis  
  
```  
HRESULT GetApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### Parámetros  
 `ppda`  
 \[out\] puntero al objeto application de depuración asociado al sitio del script.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_NOTIMPL`|El host no admite directamente la depuración.|  
  
## Comentarios  
 El método de `GetApplication` proporciona una manera para que un host inteligente defina el objeto application a que cada script pertenece.  Los motores de scripts deben intentar llamar a este método para obtener la aplicación y estación con `IProcessDebugManager::GetDefaultApplication` si se produce un error en éste.  
  
## Vea también  
 [IActiveScriptSiteDebug \(Interfaz\)](../../winscript/reference/iactivescriptsitedebug-interface.md)   
 [IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)