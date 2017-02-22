---
title: "IDebugProgram2::Continue | Microsoft Docs"
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
  - "IDebugProgram2::Continue"
helpviewer_keywords: 
  - "IDebugProgram2::Continue"
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgram2::Continue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Sigue ejecutando este programa de un estado detenido.  Conservar cualquier estado anterior de la ejecución \(como un paso\), y el inicio del programa que se ejecuta de nuevo.  
  
> [!NOTE]
>  Este método es obsoleto.  Utilice el método [Continuar](../../../extensibility/debugger/reference/idebugprocess3-continue.md) en su lugar.  
  
## Sintaxis  
  
```cpp#  
HRESULT Continue(   
   IDebugThread2* pThread  
);  
```  
  
```c#  
int Continue(   
   IDebugThread2 pThread  
);  
```  
  
#### Parámetros  
 `pThread`  
 \[in\]  un objeto de [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) que representa el subproceso.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Este método se llama este programa independientemente se están depurando cuántos programas, o qué programa generó el evento que detenía.  La implementación debe conservar el estado anterior de la ejecución \(como un paso\) y continuar la ejecución como si no había dejado antes de realizar la ejecución anterior.  Es decir, si un subproceso en este programa hace a paso\-sobre la operación y detuvo porque algún otro programa detenido y, a continuación este método se llama, el programa debe completar el original paso\-sobre la operación.  
  
> [!WARNING]
>  No envíe un evento que detiene o un evento \(sincrónico\) inmediato a [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) mientras controla esta llamada; si no el depurador puede no responder.  
  
## Vea también  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)