---
title: "IActiveScriptParseProcedure | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptParseProcedure (interfaz)"
ms.assetid: 741a35bb-5b92-489e-ba8a-a406b42125fc
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptParseProcedure
Si el motor de scripts de Windows permite que el texto del código fuente para que los procedimientos se agregan al script, implementa la interfaz de `IActiveScriptParseProcedure` .  Para los lenguajes de scripting y que no tienen ningún entorno de creación independiente, como VBScript, proporciona un mecanismo alternativo \(distinto de `IActiveScriptParse` o de `IPersist`\*\) para agregar procedimientos de script al espacio de nombres.  
  
## métodos en el orden de Vtable  
  
|||  
|-|-|  
|Método|Descripción|  
|[IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)|Analiza el procedimiento de código determinado y agrega el procedimiento al espacio de nombres.|  
  
## Vea también  
 [Active Script \(Interfaces\)](../../winscript/reference/active-script-interfaces.md)