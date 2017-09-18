---
title: "IDebugMemoryContext2::Add | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMemoryContext2::Add"
helpviewer_keywords: 
  - "IDebugMemoryContext2::Add (método)"
  - "Add (método)"
ms.assetid: 3c47e646-ce9e-4dd3-8f1a-6dbd3827d407
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugMemoryContext2::Add
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Agrega el valor especificado al contexto actual y devuelve un nuevo contexto.  
  
## Sintaxis  
  
```cpp#  
HRESULT Add(   
   UINT64                 dwCount,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```c#  
int Add(  
   ulong                    dwCount,   
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### Parámetros  
 `dwCount`  
 \[in\]  El valor que se va a agregar al contexto actual.  
  
 `ppMemCxt`  
 \[out\]  devuelve un nuevo objeto de [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) .  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Un contexto de memoria es una dirección, por lo que al agregar un valor a una dirección genera una nueva dirección que requiera una nueva interfaz de contexto.  
  
 Este método debe generar siempre un nuevo contexto, aunque la dirección resultante está fuera del espacio de memoria asociada con este contexto.  La única excepción a esto es si ninguna memoria se puede asignar para el nuevo contexto o si `ppMemCxt` es un valor NULL \(que es un error\).  
  
## Vea también  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)