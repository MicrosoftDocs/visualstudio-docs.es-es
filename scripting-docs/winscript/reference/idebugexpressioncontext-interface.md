---
title: "IDebugExpressionContext (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExpressionContext Interface
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugExpressionContext (interfaz)"
ms.assetid: 52af82e8-0dec-49e2-a7f3-d00f66ca1401
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpressionContext (Interfaz)
Representa un contexto donde se pueden evaluar las expresiones.  El objeto de marco de pila implementa esta interfaz.  
  
 Además de los métodos heredados de `IUnknown`, la interfaz `IDebugExpressionContext` expone los métodos siguientes.  
  
## métodos en el orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugExpressionContext::ParseLanguageText](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md)|Crea una expresión de depuración para el texto especificado.|  
|[IDebugExpressionContext::GetLanguageInfo](../../winscript/reference/idebugexpressioncontext-getlanguageinfo.md)|Devuelve un nombre y GUID del lenguaje que posee este contexto.|