---
title: "IDebugCanStopEvent2::CanStop | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCanStopEvent2::CanStop"
helpviewer_keywords: 
  - "IDebugCanStopEvent2::CanStop"
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCanStopEvent2::CanStop
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Notifica al motor de depuración \(DE\) si detener en la ubicación actual del código o simplemente continuar la ejecución.  
  
## Sintaxis  
  
```cpp#  
HRESULT CanStop (   
   BOOL fCanStop  
);  
```  
  
```c#  
int CanStop (   
   int fCanStop  
);  
```  
  
#### Parámetros  
 `fCanStop`  
 \[in\]  Cero \(`TRUE`\) si el OF se detiene en la ubicación actual del código; si no, cero \(`FALSE`\).  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 El receptor de este evento normalmente llama al método de [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) para determinar la razón que el OF desea detener, y después llamar al método de `IDebugCanStopEvent2::CanStop` con la respuesta adecuada.  
  
 Si el OF detiene, envía un evento que describe la razón de detenerse.  Normalmente hay dos eventos que se envían, usuario o una interrupción de la señal representada por la interfaz de [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) , y un evento de punto de interrupción representado por la interfaz de [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) .  
  
## Vea también  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)