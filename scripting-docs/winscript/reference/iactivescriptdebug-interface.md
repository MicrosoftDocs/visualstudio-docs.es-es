---
title: "IActiveScriptDebug (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptDebug (interfaz)"
ms.assetid: e3e28cba-ee08-4a52-973a-b74be488c348
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptDebug (Interfaz)
Implementado por los motores de scripts que admiten la depuración.  Normalmente, un objeto que implementa la interfaz de `IActiveScriptDebug` también implementa la interfaz de `IActiveScript` .  Si éste es el caso, llame al método de `IActiveScript::QueryInterface` para obtener la interfaz de `IActiveScriptDebug` .  
  
 La interfaz de `IActiveScriptDebug` proporciona los medios para:  
  
-   Host inteligentes adopte el control administración de documentos.  
  
-   Administrador de depuración para sincronizar la depuración de motores de scripts.  
  
 Además de los métodos heredados de `IUnknown`, la interfaz `IActiveScriptDebug` expone los métodos siguientes.  
  
## métodos en el orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScriptDebug::GetScriptTextAttributes](../../winscript/reference/iactivescriptdebug-getscripttextattributes.md)|Devuelve los atributos de texto de un bloque arbitrario de texto del script.|  
|[IActiveScriptDebug::GetScriptletTextAttributes](../../winscript/reference/iactivescriptdebug-getscriptlettextattributes.md)|Devuelve los atributos de texto para un scriptlet arbitrario.|  
|[IActiveScriptDebug::EnumCodeContextsOfPosition](../../winscript/reference/iactivescriptdebug-enumcodecontextsofposition.md)|Delegados a `IDebugDocumentContext::EnumCodeContexts`.|