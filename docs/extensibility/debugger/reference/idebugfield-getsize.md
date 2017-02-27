---
title: "IDebugField::GetSize | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugField::GetSize"
helpviewer_keywords: 
  - "IDebugField::GetSize (método)"
ms.assetid: 73329924-3751-4f44-af54-5986b7943374
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugField::GetSize
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Este método obtiene el tamaño de un campo, en bytes.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetSize(   
   DWORD* pdwSize  
);  
```  
  
```c#  
int GetSize(  
   out uint pdwSize  
);  
```  
  
#### Parámetros  
 `pdwSize`  
 \[out\]  Devuelve el tamaño.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Todos los campos tienen un tipo y todos los tipos tienen un tamaño.  Por ejemplo, un campo con un tipo de byte tiene un tamaño de 1 bytes.  
  
## Vea también  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)