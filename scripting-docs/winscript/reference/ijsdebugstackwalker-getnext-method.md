---
title: "IJsDebugStackWalker::GetNext (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugStackWalker.GetNext
apilocation: jscript9diag.dll
ms.assetid: 0b124768-50d3-4a69-876c-1aa337839a4e
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugStackWalker::GetNext (M&#233;todo)
Obtiene el fotograma siguiente.  
  
## Sintaxis  
  
```  
HRESULT GetNext(  
   IJsDebugFrame **ppFrame  
);  
```  
  
#### Parámetros  
 `ppFrame`  
 \[out\] Objeto que representa el marco de pila.  
  
## Valor devuelto  
  
## Comentarios  
 Devuelve E\_JsDEBUG\_OUTSIDE\_OF\_VM cuando no se van a enumerar más marcos de pila  
  
## Requisitos  
 **Encabezado:** jscript9diag.h  
  
## Vea también  
 [IJsDebugStackWalker \(Interfaz\)](../../winscript/reference/ijsdebugstackwalker-interface.md)