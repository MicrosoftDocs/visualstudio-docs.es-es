---
title: "IDebugProcess2::CauseBreak | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2::CauseBreak"
helpviewer_keywords: 
  - "IDebugProcess2::CauseBreak"
ms.assetid: efda8865-2319-4d53-90bf-6d9d74cd5195
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcess2::CauseBreak
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Las solicitudes que el siguiente programa que es ejecutar código en este alto de proceso y envía un objeto de evento de [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) .  
  
## Sintaxis  
  
```cpp#  
HRESULT CauseBreak(   
   void  
);  
```  
  
```c#  
int CauseBreak();  
```  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)