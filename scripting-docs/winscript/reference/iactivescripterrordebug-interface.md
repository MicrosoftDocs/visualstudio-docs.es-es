---
title: "IActiveScriptErrorDebug (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptErrorDebug (interfaz)"
ms.assetid: e5d50427-c033-4138-ac6e-3b2dfb3b750a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptErrorDebug (Interfaz)
Proporciona información de contexto del documento para los errores de compilación y excepciones en tiempo de ejecución.  El método de `IActiveScriptError::QueryInterface` admite la interfaz de `IActiveScriptErrorDebug` .  
  
 Además de los métodos heredados de `IActiveScriptError`, la interfaz `IActiveScriptErrorDebug` expone los métodos siguientes.  
  
## métodos en el orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScriptErrorDebug::GetDocumentContext](../../winscript/reference/iactivescripterrordebug-getdocumentcontext.md)|Proporciona el contexto del documento para este error.|  
|[IActiveScriptErrorDebug::GetStackFrame](../../winscript/reference/iactivescripterrordebug-getstackframe.md)|Proporciona el marco de pila que esté en efecto para los errores del runtime.|