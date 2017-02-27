---
title: "IDebugField::GetType | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugField::GetType"
helpviewer_keywords: 
  - "IDebugField::GetType (método)"
ms.assetid: b3cdec9f-ef7b-44d0-a775-d17ef7eae968
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugField::GetType
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

este método obtiene el tipo de campo.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetType(   
   IDebugField** ppType  
);  
```  
  
```c#  
int GetType(  
   out IDebugField ppType  
);  
```  
  
#### Parámetros  
 `ppType`  
 \[out\]  devuelve el tipo de campo como otro objeto de [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)