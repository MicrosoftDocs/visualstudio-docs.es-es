---
title: "IDebugThread2::Resume | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugThread2::Resume"
helpviewer_keywords: 
  - "IDebugThread2::Resume"
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugThread2::Resume
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

reanuda la ejecución de un subproceso.  
  
## Sintaxis  
  
```cpp#  
HRESULT Resume (   
   DWORD *pdwSuspendCount  
);  
```  
  
```c#  
int Resume (   
   out uint pdwSuspendCount  
);  
```  
  
#### Parámetros  
 `pdwSuspendCount`  
 \[out\]  Devuelve el valor de suspensión después de la operación resume.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Cada llamada a este método disminuye el recuento de suspensión hasta alcanzar 0 en el que el tiempo, ejecución se reanude realmente.  Este valor de suspensión se muestra en la ventana de depuración de **Subprocesos** .  
  
 Para cada llamada a este método, debe haber una llamada anterior al método de [Suspender](../../../extensibility/debugger/reference/idebugthread2-suspend.md) .  El valor de suspensión determina cuántas veces se haya llamado al método de `IDebugThread2::Suspend` hasta ahora.  
  
## Vea también  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Suspender](../../../extensibility/debugger/reference/idebugthread2-suspend.md)