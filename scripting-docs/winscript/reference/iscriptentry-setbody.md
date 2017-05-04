---
title: "IScriptEntry::SetBody | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.SetBody
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::SetBody"
ms.assetid: 719062e4-98e4-4a7b-946d-6e5dbbcc5225
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IScriptEntry::SetBody
Establece el texto incluido en el cuerpo de un bloque de script de `IScriptEntry` o un scriptlet de `IScriptScriptlet` .  
  
## Sintaxis  
  
```  
HRESULT SetBody(  
   LPCOLESTR          psz  
);  
```  
  
#### Parámetros  
 `psz`  
 \[in\] For al bloque de script de `IScriptEntry` , `psz` es el texto incluido en las etiquetas script.  
  
 Para un bloque de la función de `IScriptEntry` , `psz` es el cuerpo de la función.  
  
 Para un objeto de `IScriptScriptlet` \(que se deriva de `IScriptEntry`\), `psz` es el texto del script de scriptlet.  
  
## Valor devuelto  
 Interfaz `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
  
## Vea también  
 [IScriptEntry \(Interfaz\)](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)