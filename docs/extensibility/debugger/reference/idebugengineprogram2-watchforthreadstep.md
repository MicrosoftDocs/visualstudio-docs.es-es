---
title: "IDebugEngineProgram2::WatchForThreadStep | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngineProgram2::WatchForThreadStep"
helpviewer_keywords: 
  - "IDebugEngineProgram2::WatchForThreadStep"
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugEngineProgram2::WatchForThreadStep
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Observe que la ejecución \(o detiene el inspeccionar la ejecución\) aparezcan en el subproceso especificado.  
  
## Sintaxis  
  
```cpp#  
HRESULT WatchForThreadStep(   
   IDebugProgram2* pOriginatingProgram,  
   DWORD           dwTid,  
   BOOL            fWatch,  
   DWORD           dwFrame  
);  
```  
  
```c#  
int WatchForThreadStep(   
   IDebugProgram2 pOriginatingProgram,  
   uint           dwTid,  
   int            fWatch,  
   uint           dwFrame  
);  
```  
  
#### Parámetros  
 `pOriginatingProgram`  
 \[in\]  Un objeto de [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) que representa el programa que es ejecutado.  
  
 `dwTid`  
 \[in\]  Especifica el identificador de subproceso inspeccionar.  
  
 `fWatch`  
 \[in\]  Cero \(`TRUE`\) significa que observa para la ejecución del subproceso identificado por `dwTid`; si no, cero \(`FALSE`\) significa detención que observa para la ejecución en `dwTid`.  
  
 `dwFrame`  
 \[in\]  Especifica un índice de cuadro que controla el tipo de paso.  Cuando éste es valor es cero \(0\), el tipo de paso es “paso en” y el programa debe detener siempre que el subproceso identificado por `dwTid` se ejecute.  Cuando `dwFrame` es distinto de cero, el tipo de paso es “paso sobre” y el programa debe detener sólo si el subproceso identificado por `dwTid` se ejecuta en un cuadro cuyo índice sea igual o superior en la pila que `dwFrame`.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Cuando el administrador \(SDM\) de depuración de sesión un programa, identificado por el parámetro de `pOriginatingProgram` , se notifican al resto de los programas asociados llamando a este método.  
  
 Este método sólo es aplicable al paso de mismo\-subproceso.  
  
## Vea también  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)