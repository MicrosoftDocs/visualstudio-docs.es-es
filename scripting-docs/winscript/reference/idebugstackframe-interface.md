---
title: "IDebugStackFrame (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugStackFrame (interfaz)"
ms.assetid: e95c1b4f-17c1-490c-a56b-c25fa45d4822
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugStackFrame (Interfaz)
Representa un marco de pila lógico en la pila del subproceso.  Llame al método de `IDebugStackFrame::QueryInterface` para obtener la interfaz de `IDebugExpressionContext` , que permite la evaluación y las ventanas inspección de la expresión.  
  
 Además de los métodos heredados de `IUnknown`, la interfaz `IDebugStackFrame` expone los métodos siguientes.  
  
## métodos en el orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugStackFrame::GetCodeContext](../../winscript/reference/idebugstackframe-getcodecontext.md)|Devuelve el contexto del código de la actual asociado al marco de pila.|  
|[IDebugStackFrame::GetDescriptionString](../../winscript/reference/idebugstackframe-getdescriptionstring.md)|Devuelve una corta o una descripción textual larga del marco de pila.|  
|[IDebugStackFrame::GetLanguageString](../../winscript/reference/idebugstackframe-getlanguagestring.md)|Devuelve una corta o una descripción textual larga del lenguaje.|  
|[IDebugStackFrame::GetThread](../../winscript/reference/idebugstackframe-getthread.md)|Devuelve el subproceso asociado a este marco de pila.|  
|[IDebugStackFrame::GetDebugProperty](../../winscript/reference/idebugstackframe-getdebugproperty.md)|Devuelve un explorador de propiedades para el marco actual.|