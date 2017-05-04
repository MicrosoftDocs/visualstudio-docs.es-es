---
title: "DebugStackFrameDescriptor (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: DebugStackFrameDescriptor
apilocation: scrobj.dll
helpviewer_keywords: 
  - "DebugStackFrameDescriptor (estructura)"
ms.assetid: a86bcb99-41e4-4a26-a1dd-e1458fb73139
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# DebugStackFrameDescriptor (Estructura)
Enumera los marcos de pila y la salida de las combinaciones de varios enumeradores en el mismo subproceso.  
  
## Sintaxis  
  
```  
typedef struct tagDebugStackFrameDescriptor {  
   IDebugStackFrame *pdsf;  
   DWORD_PTR        dwMin;  
   DWORD_PTR        dwLim;  
   BOOL             fFinal;  
   IUnknown         *punkFinal;  
} DebugStackFrameDescriptor;  
```  
  
## Members  
 `pdsf`  
 El objeto de marco de pila.  
  
 `dwMin`  
 Una representación equipo\- dependiente de rango inferior de direcciones físicas asociado a este marco de pila.  
  
 `dwLim`  
 Una representación equipo\- dependiente de rango superior de direcciones físicas asociado a este marco de pila.  
  
 `fFinal`  
 Marcadores de marcado que indica que se procesa el cuadro.  
  
 `punkFinal`  
 Si este parámetro no es `NULL`, combinación actual de enumerador debe detener y un nuevo debe iniciar.  El objeto indica cómo iniciar la nueva enumeración.  
  
## Comentarios  
 El administrador de la depuración utiliza esta estructura para ordenar los marcos de pila de los motores de scripts.  Por convención, las pilas crecen abajo.  Por consiguiente, en las arquitecturas donde las pilas crecen, direcciones deben dos\- ser complementadas.  
  
## Vea también  
 [Active Script Debugger \(Constantes, enumeraciones y estructuras\)](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)