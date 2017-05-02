---
title: "IDebugApplication::HandleRuntimeError | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.HandleRuntimeError
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::HandleRuntimeError"
ms.assetid: f8f3bbaf-09e5-4d01-8a35-f380bc7ff8ed
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::HandleRuntimeError
Hace que el subproceso actual para bloquear y envía una notificación de error al depurador el IDE.  
  
## Sintaxis  
  
```  
HRESULT HandleRuntimeError(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   IActiveScriptSite*        pScriptSite,  
   BREAKRESUMEACTION*        pbra,  
   ERRORRESUMEACTION*        perra,  
   BOOL*                     pfCallOnScriptError  
);  
```  
  
#### Parámetros  
 `pErrorDebug`  
 \[in\] error a El que se produjo.  
  
 `pScriptSite`  
 \[in\] sitio de script del subproceso.  
  
 `pbra`  
 \[out\] acción para tomar cuando el depurador reanuda la aplicación.  
  
 `perra`  
 \[out\] acción para tomar cuando el depurador reanuda la aplicación si hay un error.  
  
 `pfCallOnScriptError`  
 \[out\] marcado que es `TRUE` si el motor llama al método de `IActiveScriptSite::OnScriptError` .  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Un motor de lenguaje llama a este método en el contexto de un subproceso que produce un error en tiempo de ejecución.  Este método hace que el subproceso actual para bloquear y envía una notificación de error se envía al depurador el IDE.  Cuando el depurador IDE reanuda la aplicación, retornos de este método con la acción que se realizarán.  
  
> [!NOTE]
>  Mientras que en el error en tiempo de ejecución, el motor de idioma se puede llamar el subproceso para realizar tareas como enumera los marcos de pila o evaluar las expresiones.  
  
## Vea también  
 [IDebugApplication \(Interfaz\)](../../winscript/reference/idebugapplication-interface.md)   
 [IActiveScriptErrorDebug \(Interfaz\)](../../winscript/reference/iactivescripterrordebug-interface.md)   
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)   
 [BREAKRESUMEACTION \(Enumeración\)](../../winscript/reference/breakresumeaction-enumeration.md)   
 [ERRORRESUMEACTION \(Enumeración\)](../../winscript/reference/errorresumeaction-enumeration.md)