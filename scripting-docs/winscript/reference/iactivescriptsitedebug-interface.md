---
title: "IActiveScriptSiteDebug (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptSiteDebug (interfaz)"
ms.assetid: 2557ee09-688b-4c03-a821-180c24dfa0e6
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteDebug (Interfaz)
Hospeda inteligentes implementan la interfaz de `IActiveScriptSiteDebug` para realizar la administración de documentos y para participar en la depuración.  El objeto de `IActiveScriptSite` normalmente proporciona una implementación de la interfaz de `IActiveScriptSiteDebug` .  Si se hace esto, llame al método de `IActiveScriptSite::QueryInterface` para obtener la interfaz de `IActiveScriptSiteDebug` .  
  
 Además de los métodos heredados de `IUnknown`, la interfaz `IActiveScriptSiteDebug` expone los métodos siguientes.  
  
## métodos en el orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScriptSiteDebug::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug-getdocumentcontextfromposition.md)|Utilizado por el motor del lenguaje para delegar `IDebugCodeContext::GetSourceContext`.|  
|[IActiveScriptSiteDebug::GetApplication](../../winscript/reference/iactivescriptsitedebug-getapplication.md)|Devuelve el objeto application de depuración asociado a este sitio de script.|  
|[IActiveScriptSiteDebug::GetRootApplicationNode](../../winscript/reference/iactivescriptsitedebug-getrootapplicationnode.md)|Obtiene el nodo de la aplicación en el que los documentos de script deben agregarse.|  
|[IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md)|Permite que un host inteligente determine cómo controlar errores en tiempo de ejecución.|