---
title: "IDebugThread2::Suspend | Microsoft Docs"
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
  - "IDebugThread2::Suspend"
helpviewer_keywords: 
  - "IDebugThread2::Suspend"
ms.assetid: 1e20be85-aa12-48de-bb83-0bf0976e99ae
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugThread2::Suspend
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

suspende un subproceso.  
  
## Sintaxis  
  
```cpp#  
HRESULT Suspend (   
   DWORD *pdwSuspendCount  
);  
```  
  
```c#  
HRESULT Suspend (   
   out uint pdwSuspendCount  
);  
```  
  
#### Parámetros  
 `pdwSuspendCount`  
 \[out\]  Devuelve el valor de suspensión después de la operación de suspensión.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Cada llamada a este método aumenta el recuento de suspensión de 0.  Este valor de suspensión se muestra en la ventana de depuración de **Subprocesos** .  
  
 Para cada llamada a este método, debe haber una llamada al método de [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) .  
  
## Vea también  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)