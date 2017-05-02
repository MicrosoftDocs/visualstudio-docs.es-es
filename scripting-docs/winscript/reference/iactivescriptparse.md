---
title: "IActiveScriptParse | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptParse (interfaz)"
ms.assetid: 8c967d70-f582-4f64-9e79-49f40c4dcb7c
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptParse
Si el motor de script de Windows permite el texto sin formato codifique los scriptletes que se van a agregar al script o permite que el texto de la expresión se evalúa en tiempo de ejecución, implementa la interfaz de `IActiveScriptParse` .  Para los lenguajes de scripting y que no tienen ningún entorno de creación independiente, como VBScript, proporciona un mecanismo alternativo \(distinto de `IPersist*`\) para obtener código de script del motor de script, y asociar los fragmentos de script a varios eventos de objeto.  
  
## métodos en el orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScriptParse::InitNew](../../winscript/reference/iactivescriptparse-initnew.md)|Inicializa el motor de script.|  
|[IActiveScriptParse::AddScriptlet](../../winscript/reference/iactivescriptparse-addscriptlet.md)|Agrega un scriptlet de código al script.|  
|[IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)|Analiza el scriptlet especificado de código, agregando declaraciones del espacio de nombres y la evaluación codificados según corresponda.|  
  
## Vea también  
 [Active Script \(Interfaces\)](../../winscript/reference/active-script-interfaces.md)