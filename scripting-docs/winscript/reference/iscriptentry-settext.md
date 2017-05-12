---
title: "IScriptEntry::SetText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.SetText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "ISetEntry::SetText"
ms.assetid: 4605481b-7707-43d1-ab78-a9207d0cf6fe
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptEntry::SetText
Establece el texto que corresponde a un bloque de script de `IScriptEntry` , o el código fuente que contenga un controlador de eventos de `IScriptScriptlet` .  
  
## Sintaxis  
  
```  
HRESULT SetText(  
   LPCOLESTR          psz  
);  
```  
  
#### Parámetros  
 `psz`  
 \[in\] texto del bloque de script de `IScriptEntry` , o el código fuente del controlador de eventos `IScriptScriptlet` .  
  
## Valor devuelto  
 Interfaz `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
  
## Vea también  
 [IScriptEntry \(Interfaz\)](../../winscript/reference/iscriptentry-interface.md)