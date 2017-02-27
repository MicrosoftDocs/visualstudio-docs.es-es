---
title: "IDebugField::GetKind | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugField::GetKind"
helpviewer_keywords: 
  - "IDebugField::GetKind (método)"
ms.assetid: e7c9c60a-8e55-4ecc-aa63-0c814a1e92cc
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugField::GetKind
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Este método obtiene el tipo de campo.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetKind(   
   FIELD_KIND* pdwKind  
);  
```  
  
```c#  
int GetKind(  
   out enum_FIELD_KIND pdwKind  
);  
```  
  
#### Parámetros  
 `pdwKind`  
 \[out\]  Devuelve el tipo de campo como una combinación de constantes de [FIELD\_KIND](../../../extensibility/debugger/reference/field-kind.md) .  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [FIELD\_KIND](../../../extensibility/debugger/reference/field-kind.md)