---
title: "IRemoteDebugApplication::GetName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplication.GetName
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplication::GetName"
ms.assetid: 3a8e8a4b-d7d4-40e5-97a1-f6d18db2e9c4
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplication::GetName
Devuelve el nombre de este nodo de la aplicación.  
  
## Sintaxis  
  
```  
HRESULT GetName(  
   BSTR*  pbstrName  
);  
```  
  
#### Parámetros  
 `pbstrName`  
 \[out\] nombre de este nodo de la aplicación.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método devuelve el nombre de este nodo de la aplicación.  
  
## Vea también  
 [IRemoteDebugApplication \(Interfaz\)](../../winscript/reference/iremotedebugapplication-interface.md)