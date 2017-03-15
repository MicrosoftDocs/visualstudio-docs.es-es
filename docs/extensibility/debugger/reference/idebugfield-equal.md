---
title: "IDebugField::Equal | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugField::Equal"
helpviewer_keywords: 
  - "IDebugField::Equal (método)"
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugField::Equal
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Este método compara el campo especificado para la igualdad.  
  
## Sintaxis  
  
```cpp#  
HRESULT Equal(   
   IDebugField* pField  
);  
```  
  
```c#  
int Equal(  
   IDebugField pField  
);  
```  
  
#### Parámetros  
 `pField`  
 \[in\]  El campo a comparar this.  
  
## Valor devuelto  
 Si los campos son iguales, devuelve `S_OK`.  si los campos son diferentes, devuelve `S_FALSE.` Otherwise, devuelve un código de error.  
  
## Vea también  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)