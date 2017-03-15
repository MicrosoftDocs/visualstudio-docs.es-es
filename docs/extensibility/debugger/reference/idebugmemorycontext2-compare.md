---
title: "IDebugMemoryContext2::Compare | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMemoryContext2::Compare"
helpviewer_keywords: 
  - "IDebugMemoryContext2::Compare (método)"
  - "Compare (método)"
ms.assetid: c51b5128-848e-4d8e-b2e9-1161339763c3
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugMemoryContext2::Compare
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Compara el contexto de memoria a cada contexto en la matriz especificada de la manera indicada por comparan los marcadores, devolviendo un índice del primer contexto correspondiente.  
  
## Sintaxis  
  
```cpp#  
HRESULT Compare(   
   CONTEXT_COMPARE        compare,  
   IDebugMemoryContext2** rgpMemoryContextSet,  
   DWORD                  dwMemoryContextSetLen,  
   DWORD*                 pdwMemoryContext  
);  
```  
  
```c#  
int Compare(  
   enum_CONTEXT_COMPARE   compare,   
   IDebugMemoryContext2[] rgpMemoryContextSet,   
   uint                   dwMemoryContextSetLen,   
   out uint               pdwMemoryContext  
);  
```  
  
#### Parámetros  
 `compare`  
 \[in\]  Un valor de enumeración de [CONTEXT\_COMPARE](../../../extensibility/debugger/reference/context-compare.md) que determina el tipo de comparación.  
  
 `rgpMemoryContextSet`  
 \[in\]  Una matriz de referencias a objetos de [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) a comparar con.  
  
 `dwMemoryContextSetLen`  
 \[in\]  El número de contextos de la matriz de `rgpMemoryContextSet` .  
  
 `pdwMemoryContext`  
 \[out\]  Devuelve el índice del primer contexto de memoria que satisface la comparación.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  Devuelve `E_COMPARE_CANNOT_COMPARE` si los dos contextos no pueden compararse.  
  
## Comentarios  
 Un motor de depuración \(DE\) no tiene que admitir todos los tipos de comparaciones, pero debe admitir por lo menos `CONTEXT_EQUAL`, `CONTEXT_LESS_THAN`, `CONTEXT_GREATER_THAN` y `CONTEXT_SAME_SCOPE`.  
  
## Vea también  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)   
 [CONTEXT\_COMPARE](../../../extensibility/debugger/reference/context-compare.md)