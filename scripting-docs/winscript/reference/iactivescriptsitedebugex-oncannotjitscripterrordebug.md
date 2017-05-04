---
title: "IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteDebugEx.OnCanNotJITScriptErrorDebug
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug"
ms.assetid: 83f81476-bf12-47f2-897d-1d37d21137d4
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
Informa al host sobre un error en tiempo de ejecución del script cuando el administrador de depuración no encuentra un Solo en el depurador del archivo de comandos de tiempo.  
  
 Para implementar un depurador del host, debe administrar [IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md).  Basado en una acción del usuario, el host puede o adjuntar el depurador y devuelven, o devuelve iniciar el depurador en el parámetro de OnScriptErrorDebug `pfEnterDebugger` .  También debe implementar esta interfaz para obtener la notificación sobre el error en tiempo de ejecución aunque no hay depuradores externos que pueden interpretarse por el administrador de la depuración.  
  
## Sintaxis  
  
```  
HRESULT OnCanNotJITScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug  
   BOOL *pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### Parámetros  
 `pErrorDebug`  
 \[in\] error en tiempo de ejecución a El que se produjo.  
  
 `pfCallOnScriptErrorWhenContinuingt`  
 \[out\] Si para llamar a [IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md) si el usuario decide continuar sin depurar.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 También debe implementar esta interfaz para obtener una notificación.  
  
## Vea también  
 [IActiveScriptSiteDebugEx \(Interfaz\)](../../winscript/reference/iactivescriptsitedebugex-interface.md)