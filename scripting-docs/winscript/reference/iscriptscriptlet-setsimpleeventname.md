---
title: "IScriptScriptlet::SetSimpleEventName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptScriptlet.SetSimpleEventName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptScriptlet::SetSimpleEventName"
ms.assetid: 7de9132e-635f-45df-9c92-83a24242b477
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IScriptScriptlet::SetSimpleEventName
Establece el nombre de evento simple que está asociado a un scriptlet.  Éste es un nombre de palabra única que no contiene ningún espacio en blanco.  
  
## Sintaxis  
  
```  
HRESULT SetSimpleEventName(  
   LPCOLESTR          psz  
);  
```  
  
#### Parámetros  
 `psz`  
 \[in\] búfer de que contiene el nombre de evento simple que se asocia el objeto de `IScriptScriptlet` .  
  
## Valor devuelto  
 Interfaz `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
  
## Vea también  
 [IScriptScriptlet \(Interfaz\)](../../winscript/reference/iscriptscriptlet-interface.md)