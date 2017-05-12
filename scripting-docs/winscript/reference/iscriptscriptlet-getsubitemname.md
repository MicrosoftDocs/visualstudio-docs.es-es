---
title: "IScriptScriptlet::GetSubItemName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptScriptlet.GetSubItemName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptScriptlet::GetSubItemName"
ms.assetid: 9ad963fc-9ce8-4b77-92c1-fb90d6307801
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptScriptlet::GetSubItemName
Devuelve el identificador pasado en el nombre completo del host del objeto de un scriptlet.  
  
## Sintaxis  
  
```  
HRESULT GetSubItemName(  
   BSTR               *pbstr  
);  
```  
  
#### Parámetros  
 `pbstr`  
 \[out\] si el nombre completo del scriptlet host tiene más de un nivel, `pbstr` devuelve la dirección del búfer de identificador del segundo nivel.  
  
 Si el nombre completo del scriptlet host tiene un nivel, `pbstr` devuelve la dirección del búfer de identificador del primer nivel.  
  
## Valor devuelto  
 Interfaz `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
  
## Vea también  
 [IScriptScriptlet \(Interfaz\)](../../winscript/reference/iscriptscriptlet-interface.md)