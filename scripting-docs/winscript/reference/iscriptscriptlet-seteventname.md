---
title: "IScriptScriptlet::SetEventName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptScriptlet.SetEventName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptScriptlet::SetEventName"
ms.assetid: 8787d58b-7deb-415b-b0e9-d2f0eb72dcf7
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IScriptScriptlet::SetEventName
Establece el nombre del evento asociado al scriptlet.  
  
## Sintaxis  
  
```  
HRESULT SetEventName(  
   LPCOLESTR          psz  
);  
```  
  
#### Parámetros  
 `psz`  
 \[in\] búfer de que contiene el nombre de evento asociado al objeto de `IScriptScriptlet` .  
  
## Valor devuelto  
 Interfaz `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
  
## Vea también  
 [IScriptScriptlet \(Interfaz\)](../../winscript/reference/iscriptscriptlet-interface.md)