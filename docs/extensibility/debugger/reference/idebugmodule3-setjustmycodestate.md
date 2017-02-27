---
title: "IDebugModule3::SetJustMyCodeState | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugModule3::SetJustMyCodeState"
helpviewer_keywords: 
  - "IDebugModule3::SetJustMyCodeState"
ms.assetid: 68f8166d-ef64-49ae-ad5e-79604f43bbd4
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugModule3::SetJustMyCodeState
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Marca el módulo es código de usuario o no.  
  
## Sintaxis  
  
```cpp#  
HRESULT SetJustMyCodeState(  
   BOOL fIsUserCode  
);  
```  
  
```c#  
int SetJustMyCodeState(  
   int fIsUserCode  
);  
```  
  
#### Parámetros  
 `fIsUserCode`  
 \[in\]  Cero \(`TRUE`\) si el módulo se considera código de usuario, cero \(`FALSE`\) si.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve el código de error.  
  
## Vea también  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)