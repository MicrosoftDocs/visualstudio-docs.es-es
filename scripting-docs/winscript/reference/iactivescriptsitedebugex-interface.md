---
title: "IActiveScriptSiteDebugEx (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptSiteDebugEx (Interfaz)"
ms.assetid: 76869378-1a7b-47bd-8cd0-acc31f91d58d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteDebugEx (Interfaz)
Implemente esta interfaz junto con la interfaz de `IActiveScriptSiteDebug` si está escribiendo un host que necesite obtener una notificación de un error en tiempo de ejecución en una aplicación y adjuntar opcionalmente la aplicación para la depuración.  El administrador de depuración proporciona notificación con `IActiveScriptDebug` si encuentra un depurador del archivo de comandos just\-in\-time en el equipo.  Si no se encuentra ningún depurador del archivo de comandos just\-in\-time, el PDM proporciona notificación con `IActiveScriptDebugEx` en su lugar.  
  
 Para obtener una notificación de un error en tiempo de ejecución, el host debe administrar [ActiveScriptSiteDebug::OnScriptErrorDebug](http://msdn.microsoft.com/es-es/cf7639f9-a699-4571-9f3a-82ef52c0b5f4).  Basado en una acción del usuario, puede decidir si adjuntar el depurador y devuelven internos, o devolver iniciar el depurador en el parámetro de OnScriptErrorDebug `pfEnterDebugger` .  
  
## métodos en el orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug](../../winscript/reference/iactivescriptsitedebugex-oncannotjitscripterrordebug.md)|Informa al host sobre un error en tiempo de ejecución del script cuando el administrador de depuración no encuentra un externo Sólo en depurador de tiempo.|