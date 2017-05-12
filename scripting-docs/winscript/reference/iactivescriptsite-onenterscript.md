---
title: "IActiveScriptSite::OnEnterScript | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.OnEnterScript
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_OnEnterScript"
ms.assetid: 1ed9178c-fe80-41c4-b74d-23b85f9cddbf
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::OnEnterScript
Informa al host que ha iniciado el motor de script ejecutando el script.  
  
## Sintaxis  
  
```  
HRESULT OnEnterScript(void);  
```  
  
## Valor devuelto  
 Devuelve `S_OK` si es correcto.  
  
## Comentarios  
 El motor de script debe llamar a este método en cada entrada o reingreso en el motor de script.  Por ejemplo, si el script a un objeto que se desencadena un evento controlado por el motor de script, el motor de script debe llamar a `IActiveScriptSite::OnEnterScript` antes de ejecutar el evento, y debe llamar al método de [IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md) después de ejecutar el evento pero antes de volver al objeto que desencadenó el evento.  Las llamadas a este método se pueden anidar.  Cada llamada a este método requiere una llamada correspondiente a `IActiveScriptSite::OnLeaveScript`.  
  
## Vea también  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)