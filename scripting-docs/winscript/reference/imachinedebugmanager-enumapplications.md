---
title: "IMachineDebugManager::EnumApplications | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IMachineDebugManager.EnumApplications
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IMachineDebugManager::EnumApplications"
ms.assetid: 5d833db4-fd9b-4e61-bebb-130faede5a77
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IMachineDebugManager::EnumApplications
Devuelve un enumerador de lista actual de aplicaciones en ejecución.  
  
## Sintaxis  
  
```  
HRESULT EnumApplications(  
   IEnumRemoteDebugApplications**  ppeda  
);  
```  
  
#### Parámetros  
 `ppeda`  
 \[out\] enumerador que contiene la lista actual de las aplicaciones en ejecución.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método devuelve un enumerador de lista actual de aplicaciones en ejecución.  El depurador IDE utiliza este método para mostrar y adjuntar las aplicaciones para fines de depuración.  
  
## Vea también  
 [IMachineDebugManager \(Interfaz\)](../../winscript/reference/imachinedebugmanager-interface.md)