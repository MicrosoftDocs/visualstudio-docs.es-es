---
title: "IActiveScriptParse::InitNew | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptParse.InitNew
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptParse_InitNew"
ms.assetid: 3a582bd6-fc0d-43a5-812f-5ea55a8517a1
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptParse::InitNew
Inicializa el motor de script.  
  
## Sintaxis  
  
```  
HRESULT InitNew(void);  
```  
  
## Valor devuelto  
 Devuelve `S_OK` si es correcto, o `E_FAIL` si se ha producido un error durante la inicialización.  
  
## Comentarios  
 Antes de que el motor de script puede utilizar, uno de los métodos siguientes debe invocarse: `IPersist*::Load`, `IPersist*::InitNew`, o `IActiveScriptParse::InitNew`.  La semántica de este método es idéntica a `IPersistStreamInit::InitNew`, en que este método indica inicializado al motor que propio del script.  Observe que no es válido llamar a `IPersist*::InitNew` o `IActiveScriptParse::InitNew` y `IPersist*::Load`, ni tampoco es válido llamar a `IPersist*::InitNew`, `IActiveScriptParse::InitNew`, o `IPersist*::Load` más de una vez.  
  
## Vea también  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)