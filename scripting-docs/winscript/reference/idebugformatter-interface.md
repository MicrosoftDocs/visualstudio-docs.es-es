---
title: "IDebugFormatter (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugFormatter (interfaz)"
ms.assetid: 022142d4-c8e1-47ae-b771-3e24953293e5
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugFormatter (Interfaz)
Permite que un idioma o el IDE personalizar la conversión entre los valores VARIANT o los tipos y las cadenas de VARTYPE.  
  
 Además de los métodos heredados de `IUnknown`, la interfaz `IDebugFormatter` expone los métodos siguientes.  
  
## métodos en el orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugFormatter::GetStringForVariant](../../winscript/reference/idebugformatter-getstringforvariant.md)|Devuelve una cadena que representa el valor VARIABLE especificado.|  
|[IDebugFormatter::GetVariantForString](../../winscript/reference/idebugformatter-getvariantforstring.md)|Devuelve un VARIANT que contiene la cadena especificada.|  
|[IDebugFormatter::GetStringForVarType](../../winscript/reference/idebugformatter-getstringforvartype.md)|Devuelve una cadena que representa el valor especificado de VARTYPE.|