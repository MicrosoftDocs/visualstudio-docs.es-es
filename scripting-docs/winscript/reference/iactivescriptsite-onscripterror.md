---
title: "IActiveScriptSite::OnScriptError | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.OnScriptError
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_OnScriptError"
ms.assetid: 5c9c85cc-21ad-4232-be83-a24cc7570108
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::OnScriptError
Informa al host que un error de ejecución producido mientras el motor ejecuta el script.  
  
## Sintaxis  
  
```  
HRESULT OnScriptError(  
    IActiveScriptError *pase  // address of error interface  
);  
```  
  
#### Parámetros  
 `pase`  
 \[in\] dirección de la interfaz de [IActiveScriptError](../../winscript/reference/iactivescripterror.md) del objeto de error.  Un host puede utilizar esta interfaz para obtener información sobre el error de ejecución.  
  
## Valor devuelto  
 Devuelve `S_OK` si el error correctamente se controló, o un código de error definido OLE de otra manera.  
  
## Vea también  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)