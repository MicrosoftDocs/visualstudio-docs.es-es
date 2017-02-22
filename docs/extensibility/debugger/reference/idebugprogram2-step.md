---
title: "IDebugProgram2::Step | Microsoft Docs"
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
  - "IDebugProgram2::Step"
helpviewer_keywords: 
  - "IDebugProgram2::Step"
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgram2::Step
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Realiza un paso.  
  
> [!NOTE]
>  Este método es obsoleto.  Utilice el método [Paso](../../../extensibility/debugger/reference/idebugprocess3-step.md) en su lugar.  
  
## Sintaxis  
  
```cpp#  
HRESULT Step(   
   IDebugThread2*  pThread,  
   STEPKIND        sk,  
   STEPUNIT        step  
);  
```  
  
```c#  
int Step(   
   IDebugThread2  pThread,  
   enum_STEPKIND  sk,  
   enum_STEPUNIT  step  
);  
```  
  
#### Parámetros  
 `pThread`  
 \[in\]  Un objeto de [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) que representa el subproceso que es ejecutado.  
  
 `sk`  
 \[in\]  Un valor de enumeración de [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) que especifica el tipo de paso.  
  
 `step`  
 \[in\]  Un valor de enumeración de [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) que especifica la unidad de paso \(por ejemplo, por la instrucción o la instrucción\).  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 En caso de que haya cualquier sincronización o comunicación entre subprocesos, otros subprocesos del programa deben ejecutarse cuando está pasando un subproceso determinado.  
  
> [!WARNING]
>  No envíe un evento que detiene o un evento \(sincrónico\) inmediato a [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) mientras controla esta llamada; si no el depurador puede no responder.  
  
## Vea también  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)