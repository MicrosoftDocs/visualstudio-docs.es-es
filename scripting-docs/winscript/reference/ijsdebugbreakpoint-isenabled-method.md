---
title: "IJsDebugBreakPoint::IsEnabled (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJSDebugBreakPoint.IsEnabled
apilocation: jscript9diag.dll
ms.assetid: 39b63f49-2a0d-41b7-a2ba-75dcb06251a9
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugBreakPoint::IsEnabled (M&#233;todo)
Determina si se habilita el punto de interrupción.  
  
## Sintaxis  
  
```  
HRESULT IsEnabled(  
   BOOL *pIsEnabled  
);  
```  
  
#### Parámetros  
 `pIsEnabled`  
 \[out\] Devuelve true si el punto de interrupción está habilitado; en caso contrario, devuelve false.  
  
## Valor devuelto  
  
## Comentarios  
 Devuelve E\_UNEXPECTED si se llama en un punto de interrupción eliminado.  
  
## Requisitos  
 **Encabezado:** jscript9diag.h  
  
## Vea también  
 [IJsDebugBreakPoint \(Interfaz\)](../../winscript/reference/ijsdebugbreakpoint-interface.md)