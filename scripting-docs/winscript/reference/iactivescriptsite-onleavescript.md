---
title: "IActiveScriptSite::OnLeaveScript | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.OnLeaveScript
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_OnLeaveScript"
ms.assetid: 79af0e22-fbe3-4fae-8a5f-7af8b857678d
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::OnLeaveScript
Informa al host que el motor de script cambia de ejecutar script.  
  
## Sintaxis  
  
```  
HRESULT OnLeaveScript(void);  
```  
  
## Valor devuelto  
 Devuelve `S_OK` si es correcto.  
  
## Comentarios  
 El motor de script debe llamar a este método antes de devolver el control a una aplicación de llamada que escribió en el motor de script.  Por ejemplo, si el script a un objeto que se desencadena un evento controlado por el motor de script, el motor de script debe llamar al método de [IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md) antes de ejecutar el evento, y debe llamar a `IActiveScriptSite::OnLeaveScript` después de ejecutar el evento antes de volver al objeto que desencadenó el evento.  Las llamadas a este método se pueden anidar.  Cada llamada a `IActiveScriptSite::OnEnterScript` requiere una llamada correspondiente a este método.  
  
## Vea también  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)