---
title: "IScriptScriptlet::GetEventName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptScriptlet.GetEventName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptScriptlet::GetEventName"
ms.assetid: 548fa650-808e-4c96-8253-5c72e67e8215
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IScriptScriptlet::GetEventName
Devuelve el nombre del evento asociado al scriptlet.  
  
## Sintaxis  
  
```  
HRESULT GetEventName(  
   BSTR               *pbstr  
);  
```  
  
#### Parámetros  
 `pbstr`  
 \[out\] búfer de que contiene el nombre de evento asociado al objeto de `IScriptScriptlet` .  
  
## Valor devuelto  
 Interfaz `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
  
## Vea también  
 [IScriptScriptlet \(Interfaz\)](../../winscript/reference/iscriptscriptlet-interface.md)