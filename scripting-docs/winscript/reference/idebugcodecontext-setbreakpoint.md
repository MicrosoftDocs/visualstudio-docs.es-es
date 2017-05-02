---
title: "IDebugCodeContext::SetBreakPoint | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugCodeContext.SetBreakPoint
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugCodeContext::SetBreakPoint"
ms.assetid: ecd42eae-66fa-40d3-9e47-08b826784108
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugCodeContext::SetBreakPoint
Obtiene o borrar un punto de interrupción en este contexto de código.  
  
## Sintaxis  
  
```  
HRESULT SetBreakPoint(  
   BREAKPOINT_STATE  bps  
);  
```  
  
#### Parámetros  
 `bps`  
 \[in\] especifica el estado de puntos de interrupción para este contexto de código.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método establece o desactiva un punto de interrupción en este contexto de código.  
  
## Vea también  
 [IDebugCodeContext \(Interfaz\)](../../winscript/reference/idebugcodecontext-interface.md)   
 [BREAKPOINT\_STATE \(Enumeración\)](../../winscript/reference/breakpoint-state-enumeration.md)