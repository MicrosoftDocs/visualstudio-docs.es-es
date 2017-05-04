---
title: "Windows Script (Hosts) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Windows Script Host, implementar hosts"
ms.assetid: 9d5f6471-b318-40f3-be01-d9cd0b1cdd47
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Windows Script (Hosts)
Al implementar el host de script de Microsoft Windows, puede suponer con seguridad que las llamadas de un motor de scripting sólo la interfaz de [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) en el contexto del subproceso base al host haga lo siguiente:  
  
-   Elija un subproceso base \(normalmente el subproceso que contiene el bucle de mensajes\).  
  
-   Crea una instancia del motor de script en el subproceso base.  
  
-   Métodos del motor de script de las llamadas desde el subproceso base, excepto si permitido específicamente, como cuando se trata de [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) y de [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md).  
  
-   Llama al objeto de envío del motor de script únicamente el subproceso base.  
  
-   Garantiza que el bucle de mensajes se ejecuta en el subproceso base si se proporciona un identificador de ventana.  
  
-   Garantiza que los objetos de los eventos del origen del modelo de objetos host únicamente en el subproceso base.  
  
 Estas reglas automáticamente van seguidas de todos los hosts de un solo subproceso.  El modelo restringido descrito anteriormente es deliberadamente bastante flexible que un host null un bloque script llamando a [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) de otro subproceso \(inicia un controlador de CTRL\+INTER o los similares\), o double un script en un nuevo subproceso utilizando [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md).  
  
## Comentarios  
 Ninguna de estas restricciones se aplican a un host que elija para implementar una interfaz libre\- escribir de [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) y un modelo de objetos libre\- con.  Un host puede utilizar la interfaz de [IActiveScript](../winscript/reference/iactivescript.md) de cualquier subproceso, sin restricciones.  
  
## Vea también  
 [Interfaces de script de Microsoft Windows: Introducción](http://msdn.microsoft.com/library/3d10169f-2984-49ef-90c6-dd89c97f1dd6)