---
title: "IJsDebugBreakPoint::Disable (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJSDebugBreakPoint.Disable
apilocation: jscript9diag.dll
ms.assetid: f6f2889c-c001-4ee5-8e3f-4f36235e4fad
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugBreakPoint::Disable (M&#233;todo)
Deshabilita punto de interrupción.  
  
## Sintaxis  
  
```  
HRESULT Disable(void);  
```  
  
## Valor devuelto  
  
## Comentarios  
 Devuelve E\_UNEXPECTED si se llama en un punto de interrupción eliminado.  Devuelve S\_FALSE si se llama en un punto de interrupción ya deshabilitado.  
  
## Requisitos  
 **Encabezado:** jscript9diag.h  
  
## Vea también  
 [IJsDebugBreakPoint \(Interfaz\)](../../winscript/reference/ijsdebugbreakpoint-interface.md)