---
title: "Constantes SCRIPTTHREADID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: SCRIPTTHREADID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "SCRIPTTHREADID"
ms.assetid: 1df9940c-ad0c-42d8-96b9-6a6abe2382e6
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Constantes SCRIPTTHREADID
Se utiliza para especificar el tipo de subproceso.  
  
## Sintaxis  
  
```  
typedef DWORD SCRIPTTHREADID;  
```  
  
## Constantes  
  
|Constante|Valor|Significado|  
|---------------|-----------|-----------------|  
|SCRIPTTHREADID\_CURRENT|0xFFFFFFFD|El subproceso que se está ejecutando actualmente.|  
|SCRIPTTHREADID\_BASE|0xFFFFFFFE|El subproceso base; es decir, el subproceso en el que el motor de script se creó instancias.|  
|SCRIPTTHREADID\_ALL|0xFFFFFFFF|Todos los subprocesos.|  
  
## Comentarios  
 `IActiveScript::InterruptScriptThread`utiliza el tipo de `SCRIPTTHREADID``IActiveScript::GetCurrentScriptThreadID`, `IActiveScript::GetScriptThreadID`, `IActiveScript::GetScriptThreadState`, y, pero las constantes pueden utilizar sólo por `IActiveScript::GetScriptThreadState` y `IActiveScript::InterruptScriptThread`.  
  
## Vea también  
 [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)   
 [IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)   
 [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)