---
title: "IDebugProperty2::GetMemoryBytes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty2::GetMemoryBytes"
helpviewer_keywords: 
  - "IDebugProperty2::GetMemoryBytes"
ms.assetid: b32042ed-7a06-4b4a-99ef-fe03b0aa61cc
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugProperty2::GetMemoryBytes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene los bytes de memoria que constituyen el valor de una propiedad.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetMemoryBytes (   
   IDebugMemoryBytes2** ppMemoryBytes  
);  
```  
  
```c#  
int GetMemoryBytes (   
   out IDebugMemoryBytes2 ppMemoryBytes  
);  
```  
  
#### Parámetros  
 `ppMemoryBytes`  
 \[out\]  Devuelve un objeto de [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) que se puede utilizar para recuperar la memoria que contiene el valor de la propiedad.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; si no devuelve un código de error.  devuelve `S_GETMEMORYBYTES_NO_MEMORY_BYTES` si no hay bytes de memoria a recuperar.  
  
## Vea también  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)