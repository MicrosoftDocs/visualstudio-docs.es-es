---
title: "IDebugBinder::GetFunctionObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBinder::GetFunctionObject"
helpviewer_keywords: 
  - "IDebugBinder::GetFunctionObject (método)"
ms.assetid: 8fb789df-8f30-420d-8ca5-bb496a6738f1
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugBinder::GetFunctionObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Este método obtiene un objeto de [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) utilizado para crear parámetros de función.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetFunctionObject(   
   IDebugFunctionObject **ppFunction  
);  
```  
  
```c#  
int GetFunctionObject(  
   out IDebugFunctionObject ppFunction  
);  
```  
  
#### Parámetros  
 `ppFunction`  
 \[out\]  Devuelve la interfaz de [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) que se utiliza para crear parámetros de función.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve S\_OK; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)