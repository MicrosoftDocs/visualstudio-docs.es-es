---
title: "IDebugThread2::SetThreadName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugThread2::SetThreadName"
helpviewer_keywords: 
  - "IDebugThread2::SetThreadName"
ms.assetid: fa934121-3f58-44dc-9c30-d3f752e44c8b
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugThread2::SetThreadName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Establece el nombre del subproceso.  
  
## Sintaxis  
  
```cpp#  
HRESULT SetThreadName (   
   LPCOLESTR pszName  
);  
```  
  
```c#  
int SetThreadName (   
   string pszName  
);  
```  
  
#### Parámetros  
 `pszName`  
 \[in\]  El nombre del subproceso.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Para obtener el nombre del subproceso, llame al método de [GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md) .  
  
## Vea también  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)