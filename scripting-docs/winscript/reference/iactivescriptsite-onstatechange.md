---
title: "IActiveScriptSite::OnStateChange | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.OnStateChange
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_OnStateChange"
ms.assetid: 3e9c5cbe-ca8e-426a-84fd-04e9c2daac7e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSite::OnStateChange
Informa al host que el motor de script ha cambiado a estados.  
  
## Sintaxis  
  
```  
HRESULT OnStateChange(  
    SCRIPTSTATE ssScriptState  // new state of engine  
);  
```  
  
#### Parámetros  
 `ssScriptState`  
 \[in\] valore que indica el nuevo estado de script.  Vea el método de [IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md) para obtener una descripción de estados.  
  
## Valor devuelto  
 Devuelve `S_OK` si es correcto.  
  
## Vea también  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)