---
title: "IScriptNode::GetLanguage | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode.GetLanguage
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::GetLanguage"
ms.assetid: 089715fd-6746-474e-94ed-2e57ee4bc0da
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# IScriptNode::GetLanguage
Devuelve el lenguaje de comandos que usa el nodo actual del script.  
  
## Sintaxis  
  
```  
HRESULT GetLanguage(  
   BSTR               *pbstr  
);  
```  
  
#### Parámetros  
 `pbstr`  
 \[out\] devuelve “JScript” si el nodo de script utiliza JScript, o “VBScript” si el nodo de script utiliza la Visual Basic scripting edition \(VBScript\).  
  
## Valor devuelto  
 Interfaz `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
  
## Vea también  
 [IScriptNode \(Interfaz\)](../../winscript/reference/iscriptnode-interface.md)