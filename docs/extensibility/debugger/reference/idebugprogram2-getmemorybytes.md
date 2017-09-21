---
title: "IDebugProgram2::GetMemoryBytes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::GetMemoryBytes"
helpviewer_keywords: 
  - "IDebugProgram2::GetMemoryBytes"
ms.assetid: 1cdedb47-caf8-468e-aaf4-163f16afb403
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProgram2::GetMemoryBytes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

recupera los bytes de memoria ocupados por el programa.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetMemoryBytes(   
   IDebugMemoryBytes2** ppMemoryBytes  
);  
```  
  
```c#  
int GetMemoryBytes(   
   out IDebugMemoryBytes2 ppMemoryBytes  
);  
```  
  
#### Parámetros  
 `ppMemoryBytes`  
 \[out\]  Devuelve un objeto de [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) que representa los bytes de memoria del programa.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Bytes de memoria como se representa por el objeto de [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) son para el programa en memoria y no ninguna la memoria asignada cuando el programa se ejecutó.  
  
## Vea también  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)