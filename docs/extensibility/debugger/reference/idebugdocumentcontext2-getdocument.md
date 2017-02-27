---
title: "IDebugDocumentContext2::GetDocument | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentContext2::GetDocument"
helpviewer_keywords: 
  - "IDebugDocumentContext2::GetDocument"
ms.assetid: c6d46c5d-ade8-4dc8-9862-8fc7876658c4
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDocumentContext2::GetDocument
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene el documento que contiene este contexto de documento.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetDocument(   
   IDebugDocument2** ppDocument  
);  
```  
  
```c#  
int GetDocument(   
   out IDebugDocument2 ppDocument  
);  
```  
  
#### Parámetros  
 `ppDocument`  
 \[out\]  Devuelve un objeto de [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) que representa el documento que contiene este contexto de documento.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Este método es para los motores de depuración que especifique documentos directamente al IDE.  De lo contrario, este método debe devolver `E_NOTIMPL`.  
  
## Vea también  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)