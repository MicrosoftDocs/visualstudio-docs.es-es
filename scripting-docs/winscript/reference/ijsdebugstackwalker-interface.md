---
title: "IJsDebugStackWalker (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 3fe30394-49c8-48e9-bde9-ffe5d79b2121
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugStackWalker (Interfaz)
Representa un rastreador de pila para un subproceso especificado.  
  
## Sintaxis  
  
```  
IJsDebugStackWalker : public IUnknown;  
```  
  
## Members  
  
### Métodos públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[IJsDebugStackWalker::GetNext \(Método\)](../../winscript/reference/ijsdebugstackwalker-getnext-method.md)|Obtiene el fotograma siguiente.|  
  
## Comentarios  
 Los rastreadores de pila solo pueden crearse mientras se detiene el destino y no son válidos una vez que se ha seguido continuando el proceso de destino.  
  
## Requisitos  
 **Encabezado:** jscript9diag.h  
  
## Vea también  
 [Referencia de interfaces de Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)