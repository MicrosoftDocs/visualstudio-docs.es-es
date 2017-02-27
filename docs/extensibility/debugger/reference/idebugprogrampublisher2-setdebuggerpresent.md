---
title: "IDebugProgramPublisher2::SetDebuggerPresent | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramPublisher2::SetDebuggerPresent"
helpviewer_keywords: 
  - "IDebugProgramPublisher2::SetDebuggerPresent"
ms.assetid: c88c3ff4-3632-4199-b5de-83c6d21bcf75
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugProgramPublisher2::SetDebuggerPresent
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Indica un editor de programa que un depurador está presente y ejecución.  
  
## Sintaxis  
  
```cpp  
HRESULT SetDebuggerPresent(  
   BOOL fDebuggerPresent  
);  
```  
  
```c#  
int SetDebuggerPresent(  
   int fDebuggerPresent  
);  
```  
  
#### Parámetros  
 `fDebuggerPresent`  
 \[in\]  Cero \(`TRUE`\) si un depurador está presente, cero \(`FALSE`\) si no es.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 La presencia o ausencia de un depurador se refleja en los datos devueltos por el método de [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) : el valor devuelto hay establecido o desactivada por una llamada anterior al método de `SetDebuggerPresent` .  
  
## Vea también  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)