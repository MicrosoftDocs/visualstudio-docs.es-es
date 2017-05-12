---
title: "IScriptScriptlet::SetSubItemName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptScriptlet.SetSubItemName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptScriptlet::SetSubItemName"
ms.assetid: 619f222f-b4c3-4c7b-9d19-e4e7037343a6
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IScriptScriptlet::SetSubItemName
Establece el identificador pasado en el nombre completo del host del objeto de un scriptlet.  
  
## Sintaxis  
  
```  
HRESULT SetSubItemName(  
   LPCOLESTR          psz  
);  
```  
  
#### Parámetros  
 `psz`  
 Si el nombre completo del scriptlet host tiene más de un nivel, `psz` es la dirección del búfer de identificador del segundo nivel.  
  
 Si el nombre completo del scriptlet host tiene un nivel, `psz` es la dirección del búfer de identificador del primer nivel.  
  
## Valor devuelto  
 Interfaz `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
  
## Vea también  
 [IScriptScriptlet \(Interfaz\)](../../winscript/reference/iscriptscriptlet-interface.md)