---
title: "IProcessDebugManager::GetDefaultApplication | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IProcessDebugManager.GetDefaultApplication
apilocation: pdm.dll
helpviewer_keywords: 
  - "IProcessDebugManager::GetDefaultApplication"
ms.assetid: 6c991faa-ea40-4d18-a1b8-6e7d0de6dd43
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IProcessDebugManager::GetDefaultApplication
Devuelve un objeto de aplicación predeterminado para el proceso actual.  
  
## Sintaxis  
  
```  
HRESULT GetDefaultApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### Parámetros  
 `ppda`  
 \[out\] objeto application de depuración para obtener esta aplicación.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método crea un nuevo objeto application de depuración y lo agrega a la lista actual de la aplicación, si es necesario.  
  
 Los motores de lenguajes deben utilizar la aplicación especificada por el método de `GetDefaultApplication` si se ejecutan en un host que no proporcione una aplicación.  
  
## Vea también  
 [IProcessDebugManager \(Interfaz\)](../../winscript/reference/iprocessdebugmanager-interface.md)