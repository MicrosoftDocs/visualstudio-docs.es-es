---
title: "IDebugDocumentPosition2::GetFileName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentPosition2::GetFileName"
helpviewer_keywords: 
  - "IDebugDocumentPosition2::GetFileName"
ms.assetid: d713635e-088f-465b-b26d-00ac971c9e86
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDocumentPosition2::GetFileName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene el nombre del archivo de código fuente que contiene la posición del documento.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetFileName(   
   BSTR* pbstrFileName  
);  
```  
  
```c#  
int GetFileName(   
   out string pbstrFileName  
);  
```  
  
#### Parámetros  
 `pbstrFileName`  
 \[out\]  Devuelve el nombre del archivo de código fuente.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Un archivo de código fuente no siempre tener un nombre de archivo \(el archivo de código fuente puede no existir en el disco, por ejemplo\).  
  
## Vea también  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)