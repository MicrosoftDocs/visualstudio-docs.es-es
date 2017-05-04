---
title: "IJsDebugProcess::CreateStackWalker (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugProcess.CreateStackWalker
apilocation: jscript9diag.dll
ms.assetid: 9d02e21d-7900-4942-8d17-cd04a2261463
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugProcess::CreateStackWalker (M&#233;todo)
Método de generador para el rastreador de pila.  
  
## Sintaxis  
  
```  
HRESULT CreateStackWalker(  
   DWORD threadId,  
   IJsDebugStackWalker **ppStackWalker  
);  
```  
  
#### Parámetros  
 `threadId`  
 \[in\] El id. del subproceso.  
  
 `ppStackWalker`  
 \[out\] Nuevo objeto rastreador de pila.  
  
## Valor devuelto  
  
## Comentarios  
 Devuelve E\_JsDEBUG\_UNKNOWN\_THREAD si el subproceso no tiene JavaScript en él.  Este método puede invocarse únicamente mientras se detiene el proceso de destino.  
  
## Requisitos  
 **Encabezado:** jscript9diag.h  
  
## Vea también  
 [IJsDebugProcess \(Interfaz\)](../../winscript/reference/ijsdebugprocess-interface.md)