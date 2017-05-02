---
title: "IJsDebugProcess (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: a7ad5525-55b7-4c68-a4f7-c508f7877712
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IJsDebugProcess (Interfaz)
Proporciona rutinas para inspeccionar y controlar el proceso de destino.  
  
## Sintaxis  
  
```  
IJsDebugProcess : public IUnknown;  
```  
  
## Miembros  
  
### Métodos públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[IJsDebugProcess::CreateBreakPoint \(Método\)](../../winscript/reference/ijsdebugprocess-createbreakpoint-method.md)|Establece el punto de interrupción en la posición del documento especificada.|  
|[IJsDebugProcess::CreateStackWalker \(Método\)](../../winscript/reference/ijsdebugprocess-createstackwalker-method.md)|Método de generador para el rastreador de pila.|  
|[IJsDebugProcess::PerformAsyncBreak \(Método\)](../../winscript/reference/ijsdebugprocess-performasyncbreak-method.md)|Pone el motor de scripts en modo de interrupción, haciendo que se detenga en la siguiente instrucción de script.|  
  
## Requisitos  
 **Encabezado:** jscript9diag.h  
  
## Vea también  
 [Referencia de interfaces de Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)