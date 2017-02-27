---
title: "IDebugActivateDocumentEvent2::GetDocument | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugActivateDocumentEvent2::GetDocument"
helpviewer_keywords: 
  - "GetDocument (método)"
  - "IDebugActivateDocumentEvent2::GetDocument (método)"
ms.assetid: b3c32f1b-f3de-409d-920d-ba7b3fa84fcd
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugActivateDocumentEvent2::GetDocument
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene el documento para activar.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetDocument (   
   IDebugDocument2** ppDoc  
);  
```  
  
```c#  
int GetDocument (   
   out IDebugDocument2 ppDoc  
);  
```  
  
#### Parámetros  
 `ppDoc`  
 \[out\]  Devuelve un objeto de [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) que representa el documento que se inicia.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)