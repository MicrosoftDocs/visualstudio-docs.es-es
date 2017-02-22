---
title: "IDebugProcess3::Continue | Microsoft Docs"
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
  - "IDebugProcess3::Continue"
helpviewer_keywords: 
  - "IDebugProcess3::Continue"
ms.assetid: 57506242-5763-4c08-adb9-8a78ce02cebb
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcess3::Continue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Sigue ejecutando este proceso de un estado detenido.  Conservar cualquier estado anterior de la ejecución \(como un paso\), y el inicio de proceso que se ejecuta de nuevo.  
  
> [!NOTE]
>  Este método se debe utilizar en lugar de [Continuar](../../../extensibility/debugger/reference/idebugprogram2-continue.md).  
  
## Sintaxis  
  
```cpp  
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
 \[in\]  Un objeto de [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) que representa el subproceso que se continúa.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve el código de error.  
  
## Comentarios  
 Este método se llama este proceso independientemente se están depurando cuántos procesos, o qué proceso generó el evento que detenía.  La implementación debe conservar el estado anterior de la ejecución \(como un paso\) y continuar la ejecución como si no había dejado antes de realizar la ejecución anterior.  Es decir, si un subproceso en este proceso estaba a paso\-sobre la operación y detuvo porque otro proceso detenido y, a continuación `Continue` se con nombre, el subproceso especificado debe completar el original paso\-sobre la operación.  
  
 **Advertencia** no envía un evento que detiene o un evento \(sincrónico\) inmediato a [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) mientras controla esta llamada; si no el depurador puede no responder.  
  
## Vea también  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)