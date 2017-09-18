---
title: "IDebugProcess2::EnumThreads | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2::EnumThreads"
helpviewer_keywords: 
  - "IDebugProcess2::EnumThreads"
ms.assetid: 05677385-7a7f-4545-8438-af00dde85db0
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcess2::EnumThreads
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

recupera una lista de todos los subprocesos que se ejecutan en el proceso.  
  
## Sintaxis  
  
```cpp#  
HRESULT EnumThreads(  
   IEnumDebugThreads2** ppEnum  
);  
```  
  
```c#  
int EnumThreads(  
   out IEnumDebugThreads2 ppEnum  
);  
```  
  
#### Parámetros  
 `ppEnum`  
 \[out\]  Devuelve un objeto de [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md) que contiene una lista de todos los subprocesos en todos los programas en el proceso.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Este método enumera los subprocesos que se ejecutan en cada programa y los combina en una vista de los subprocesos.  Un subproceso puede ejecutarse en programas varias; este método enumera ese subproceso sólo una vez.  
  
 Este método muestra una lista de los subprocesos del proceso sin duplicados.  Si no, para enumerar los subprocesos que se ejecutan en un programa concreto, utilice el método de [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) .  
  
## Vea también  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)