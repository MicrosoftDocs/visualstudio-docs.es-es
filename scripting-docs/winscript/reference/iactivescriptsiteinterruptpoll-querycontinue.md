---
title: "IActiveScriptSiteInterruptPoll::QueryContinue | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteInterruptPoll.QueryContinue
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteInterruptPoll::QueryContinue"
ms.assetid: 41ac3807-f8b4-4a0e-bcc6-556bc89f3904
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteInterruptPoll::QueryContinue
Permite que un host especificar un script que termine.  
  
## Sintaxis  
  
```  
HRESULT QueryContinue();  
```  
  
#### Parámetros  
 Este método no toma ningún parámetro.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|La llamada se realizó correctamente y el host permite que el script continúa ejecutándose.|  
|`S_FALSE`|La llamada se realizó correctamente y las solicitudes de host que el script termina.|  
  
## Comentarios  
 El script hospedado debe finalizar a menos que el valor devuelto del método de `QueryContinue` es `S_OK`.  Un valor devuelto de `S_FALSE` indica que las solicitudes de host explícitamente que el script termina.  
  
 Un host multiproceso puede utilizar el método de `IActiveScript::InterruptScriptThread` para finalizar un script.  
  
## Vea también  
 [IActiveScriptSiteInterruptPoll \(Interfaz\)](../../winscript/reference/iactivescriptsiteinterruptpoll-interface.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)