---
title: "IActiveScriptParseProcedureOld (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptParseProcedureOld
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptParseProcedureOld (interfaz)"
ms.assetid: d94b391e-4c24-46da-a01f-2c134ca4f041
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptParseProcedureOld (Interfaz)
Permite que el texto del código fuente para que los procedimientos se agregan al script.  Para los lenguajes de scripting y que no tienen un entorno de creación independiente, como VBScript, proporciona un mecanismo alternativo \(distinto de `IActiveScriptParse` o de `IPersist*`\) para agregar procedimientos de script al espacio de nombres.  
  
> [!NOTE]
>  Esta interfaz está desusada a favor de la interfaz de `IActiveScriptParseProcedure` .  
  
## Métodos  
 Además de los métodos heredados de `IUnknown`, la interfaz `IActiveScriptParseProcedureOld` expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScriptParseProcedureOld::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedureold-parseproceduretext.md)|Analiza el procedimiento de código determinado y agrega el procedimiento al espacio de nombres.|  
  
## Vea también  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)