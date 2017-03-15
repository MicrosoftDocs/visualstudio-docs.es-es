---
title: "IDebugMemoryBytes2::WriteAt | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMemoryBytes2::WriteAt"
helpviewer_keywords: 
  - "IDebugMemoryBytes2::WriteAt (método)"
  - "Método WriteAt"
ms.assetid: 61cc3704-47fa-4d9b-aa62-bb4585ac8fb1
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugMemoryBytes2::WriteAt
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Escriba el número de bytes especificado de memoria, empezando en la dirección especificada.  
  
## Sintaxis  
  
```cpp#  
HRESULT WriteAt(   
   IDebugMemoryContext2* pStartContext,  
   DWORD                 dwCount,  
   BYTE*                 rgbMemory  
);  
```  
  
```c#  
int WriteAt(  
   IDebugMemoryContext2 pStartContext,  
   uint                 dwCount,  
   byte[]               rgbMemory  
);  
```  
  
#### Parámetros  
 `pStartContext`  
 \[in\]  El objeto de [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) que especifica dónde iniciar bytes de escritura.  
  
 `dwCount`  
 \[in\]  el número de bytes a escribir.  
  
 `rgbMemory`  
 \[in\]  los bytes a escribir.  Esta matriz se asume que por lo menos bytes de `dwCount` de tamaño.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve `S_FALSE` si no que todos los bytes pueden tener tipo o devuelve un código de error \(normalmente `E_FAIL`\).  
  
## Comentarios  
 Si la dirección inicial no está dentro de la ventana memoria representada por este objeto de [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) , ninguna escribir aparece y un código de error de `E_FAIL` se devuelve \(incluso si la cantidad en la escritura se superpone en el espacio de memoria.  
  
## Vea también  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)