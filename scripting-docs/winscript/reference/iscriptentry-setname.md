---
title: "IScriptEntry::SetName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.SetName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::SetName"
ms.assetid: dfa33450-87d7-4c8e-bfd8-0cc2d6542a0e
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IScriptEntry::SetName
Para las entradas que representan un objeto único \(como una función\), establece el nombre del objeto.  
  
## Sintaxis  
  
```  
HRESULT SetName(  
   LPCOLESTR          psz  
);  
```  
  
#### Parámetros  
 `psz`  
 \[in\] nuevo nombre del objeto de `IScriptEntry` .  
  
## Valor devuelto  
 Interfaz `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
  
## Vea también  
 [IScriptEntry \(Interfaz\)](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptEntry::GetName](../../winscript/reference/iscriptentry-getname.md)