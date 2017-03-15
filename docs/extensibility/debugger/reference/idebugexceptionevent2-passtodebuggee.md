---
title: "IDebugExceptionEvent2::PassToDebuggee | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExceptionEvent2::PassToDebuggee"
helpviewer_keywords: 
  - "IDebugExceptionEvent2::PassToDebuggee"
ms.assetid: a20d0f0b-2ca0-4437-bd22-9213c81d2738
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugExceptionEvent2::PassToDebuggee
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Especifica si la excepción se debe pasar al programa que se está depurando cuando la ejecución se reanuda, o si se descarta la excepción.  
  
## Sintaxis  
  
```cpp#  
HRESULT PassToDebuggee(  
   BOOL fPass  
);  
```  
  
```c#  
int PassToDebuggee(  
   int fPass  
);  
```  
  
#### Parámetros  
 `fPass`  
 \[in\]  Cero \(`TRUE`\) si la excepción se pasa al programa que se está depurando cuando la ejecución se reanuda, o cero \(`FALSE`\) si se descarta la excepción.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Llamar a este método no produce realmente ningún código que se ejecutará en el programa que se depura.  La llamada es simplemente establecer el estado para la ejecución de código siguiente.  Por ejemplo, las llamadas al método de [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) pueden devolver `S_OK` con [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md). conjunto de campos de`dwState` a `EXCEPTION_STOP_SECOND_CHANCE`.  
  
 El IDE puede recibir el evento de [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) y llamar al método de [Continuar](../../../extensibility/debugger/reference/idebugprogram2-continue.md) .  El motor de depuración \(DE\) debe tener un comportamiento predeterminado para controlar el caso del método de `PassToDebuggee` no se denomina.  
  
## Vea también  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)   
 [Continuar](../../../extensibility/debugger/reference/idebugprogram2-continue.md)