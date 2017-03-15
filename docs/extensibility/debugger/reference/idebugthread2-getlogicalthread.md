---
title: "IDebugThread2::GetLogicalThread | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugThread2::GetLogicalThread"
helpviewer_keywords: 
  - "IDebugThread2::GetLogicalThread"
ms.assetid: bce6230e-41d4-49b7-a050-2dde5efb6805
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugThread2::GetLogicalThread
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Los motores de depuración no implementan este método.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetLogicalThread(   
   IDebugStackFrame2*     pStackFrame,  
   IDebugLogicalThread2** ppLogicalThread  
);  
```  
  
```c#  
int GetLogicalThread(   
   IDebugStackFrame2        pStackFrame,  
   out IDebugLogicalThread2 ppLogicalThread  
);  
```  
  
#### Parámetros  
 `pStackFrame`  
 \[in\]  un objeto de [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) que representa el marco de pila.  
  
 `ppLogicalThread`  
 \[out\]  Devuelve una interfaz de `IDebugLogicalThread2` que representa el subproceso lógico asociado.  Una implementación del motor de depuración debe establecer esto en un valor nulo.  
  
## Valor devuelto  
 Implementaciones `E_NOTIMPL`siempre devuelto del motor de depuración.  
  
## Vea también  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)