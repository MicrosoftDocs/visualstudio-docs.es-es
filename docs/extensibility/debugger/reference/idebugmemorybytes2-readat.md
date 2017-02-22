---
title: "IDebugMemoryBytes2::ReadAt | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMemoryBytes2::ReadAt"
helpviewer_keywords: 
  - "IDebugMemoryBytes2::ReadAt (método)"
  - "ReadAt (método)"
ms.assetid: b413684d-4155-4bd4-ae30-ffa512243b5f
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugMemoryBytes2::ReadAt
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Lee una secuencia de bytes, comenzando en una ubicación determinada.  
  
## Sintaxis  
  
```cpp#  
HRESULT ReadAt(   
   IDebugMemoryContext2* pStartContext,  
   DWORD                 dwCount,  
   BYTE*                 rgbMemory,  
   DWORD*                pdwRead,  
   DWORD*                pdwUnreadable  
);  
```  
  
```c#  
int ReadAt(  
   IDebugMemoryContext2 pStartContext,  
   uint                 dwCount,  
   byte[]               rgbMemory,  
   out uint             pdwRead,  
   ref uint             pdwUnreadable  
);  
```  
  
#### Parámetros  
 `pStartContext`  
 \[in\]  El objeto de [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) que especifica dónde iniciar bytes de lectura.  
  
 `dwCount`  
 \[in\]  El número de bytes que se va a leer.  También especifica la longitud de la matriz de `rgbMemory` .  
  
 `rgbMemory`  
 \[in, out\]  La matriz completa con los bytes leídos realmente.  
  
 `pdwRead`  
 \[out\]  devuelve el número de bytes contiguos lee realmente.  
  
 `pdwUnreadable`  
 \[in, out\]  devuelve el número de bytes ilegibles.  Puede ser un valor NULL si el cliente es irrelevante en el número de bytes ilegibles.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve S\_OK; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Si se solicitan 100 bytes y los 50 primeros son legibles, los 20 siguientes son ilegibles, y los 30 restantes son legibles, este método devuelve:  
  
 \*`pdwRead` \= 50  
  
 \*`pdwUnreadable` \= 20  
  
 En este caso, porque `*pdwRead + *pdwUnreadable < dwCount`, el llamador deben realizar una llamada adicional para leer restantes los 30 bytes de los 100 originales solicitados y el objeto de [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) pasado en el parámetro de `pStartContext` deben avanzar por 70.  
  
## Vea también  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)