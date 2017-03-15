---
title: "IEnumDebugThreads2::Reset | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugThreads2::Reset"
helpviewer_keywords: 
  - "IEnumDebugThreads2::Reset"
ms.assetid: 88980d9a-c4d6-4de4-a9ab-fb56fa71394a
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEnumDebugThreads2::Reset
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Restablece la enumeración en el primer elemento.  
  
## Sintaxis  
  
```cpp#  
HRESULT Reset(  
   void  
);  
```  
  
```c#  
int Reset();  
```  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Después de que se llame a este método, la siguiente llamada al método de [Siguiente](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md) devuelve el primer elemento de la enumeración.  
  
## Vea también  
 [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)