---
title: "IDebugMemoryContext2::Subtract | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMemoryContext2::Subtract"
helpviewer_keywords: 
  - "Restar (método)"
  - "IDebugMemoryContext2::Subtract (método)"
ms.assetid: 63df14c7-8d7e-47c1-afa7-5a1ab5d8eaba
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugMemoryContext2::Subtract
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Resta el valor especificado del contexto actual y devuelve un nuevo contexto.  
  
## Sintaxis  
  
```cpp#  
HRESULT Subtract(   
   UINT64                 dwCount,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```c#  
int Subtract(  
   ulong                    dwCount,   
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### Parámetros  
 `dwCount`  
 \[in\]  El número de bytes de memoria disminuir.  
  
 `ppMemCxt`  
 \[out\]  devuelve un nuevo objeto de [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) .  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Un contexto de memoria es una dirección, por lo que resta un valor desde una dirección genera una nueva dirección que requiera una nueva interfaz de contexto.  
  
 Este método debe generar siempre un nuevo contexto, aunque la dirección resultante está fuera del espacio de memoria asociada con este contexto.  La única excepción a esto es si ninguna memoria se puede asignar para el nuevo contexto o si `ppMemCxt` es un valor NULL \(que es un error\).  
  
## Vea también  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)