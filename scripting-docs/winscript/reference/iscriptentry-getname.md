---
title: "IScriptEntry::GetName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.GetName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::GetName"
ms.assetid: 56daa288-618f-497c-a360-7d443afd478b
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IScriptEntry::GetName
Para las entradas que representan un objeto único \(como una función\), especificado el nombre del objeto.  
  
## Sintaxis  
  
```  
HRESULT GetName(  
   BSTR               *pbstr  
);  
```  
  
#### Parámetros  
 `pbstr`  
 \[out\] nombre del objeto representado por el bloque de script de `IScriptEntry` .  Si una entrada no representa un único objeto, se devuelve NULL.  
  
 Las entradas secundarias representan un único objeto de función.  
  
## Valor devuelto  
 Interfaz `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
  
## Vea también  
 [IScriptEntry \(Interfaz\)](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptNode:: CreateChildEntry](../../winscript/reference/iscriptnode-createchildentry.md)