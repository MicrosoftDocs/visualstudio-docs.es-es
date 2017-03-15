---
title: "IDebugReference2::SetReferenceType | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugReference2::SetReferenceType"
helpviewer_keywords: 
  - "IDebugReference2::SetReferenceType"
ms.assetid: 5854a172-ea82-481c-97d9-c7fc16923d44
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugReference2::SetReferenceType
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

establece el tipo de referencia.  Reservado para un uso futuro.  
  
## Sintaxis  
  
```cpp#  
HRESULT SetReferenceType (   
   REFERENCE_TYPE dwRefType  
);  
```  
  
```c#  
int SetReferenceType (   
   enum_REFERENCE_TYPE dwRefType  
);  
```  
  
#### Parámetros  
 `dwRefType`  
 \[in\]  Un valor de enumeración de [REFERENCE\_TYPE](../../../extensibility/debugger/reference/reference-type.md) que especifica el tipo de referencia.  
  
## Valor devuelto  
 Siempre devuelve `E_NOTIMPL`.  
  
## Vea también  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [REFERENCE\_TYPE](../../../extensibility/debugger/reference/reference-type.md)