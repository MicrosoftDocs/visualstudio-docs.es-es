---
title: "IDebugStackFrame2::GetDocumentContext | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugStackFrame2::GetDocumentContext"
helpviewer_keywords: 
  - "IDebugStackFrame2::GetDocumentContext"
ms.assetid: 69e81439-1238-4f18-9028-6fd1c1ba5e4a
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugStackFrame2::GetDocumentContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene el contexto del documento para este marco de pila.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetDocumentContext (   
   IDebugDocumentContext2** ppCxt  
);  
```  
  
```c#  
int GetDocumentContext (   
   out IDebugDocumentContext2 ppCxt  
);  
```  
  
#### Parámetros  
 `ppCxt`  
 \[out\]  Devuelve un objeto de [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) que representa la posición actual en un documento de origen.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Este método es más rápido que llamando al método de [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md) y después llamando al método de [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) en el contexto del código.  Sin embargo, no se garantiza que cada motor \(DE\) de depuración implementa este método.  
  
## Vea también  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)