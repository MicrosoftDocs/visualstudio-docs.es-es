---
title: "IDebugProcess3::Step | Microsoft Docs"
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
  - "IDebugProcess3::Step"
helpviewer_keywords: 
  - "IDebugProcess3::Step"
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcess3::Step
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Hace que el proceso a la instrucción o la instrucción de paso uno.  
  
> [!NOTE]
>  Este método se debe utilizar en lugar de [Paso](../../../extensibility/debugger/reference/idebugprogram2-step.md).  
  
## Sintaxis  
  
```cpp  
HRESULT Step(  
   IDebugThread2* pThread,  
   STEPKIND       sk,  
   STEPUNIT       step,  
);  
```  
  
```c#  
int Step(  
   IDebugThread2 pThread,   
   enum_STEPKIND sk,   
   enum_STEPUNIT step  
);  
```  
  
#### Parámetros  
 `pThread`  
 \[in\]  Un objeto de [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) que representa el subproceso que es ejecutado.  
  
 `sk`  
 \[in\]  uno de los valores de [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) .  
  
 `step`  
 \[in\]  uno de los valores de [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) .  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve S\_OK; si no devuelve un código de error.  
  
## Comentarios  
 En caso de que haya cualquier sincronización o comunicación entre subprocesos, otros subprocesos del proceso deben ejecutarse cuando está pasando un subproceso determinado.  
  
 **Advertencia** no envía un evento que detiene o un evento \(sincrónico\) inmediato a [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) mientras controla esta llamada; si no el depurador puede no responder.  
  
## Vea también  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)   
 [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)   
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)