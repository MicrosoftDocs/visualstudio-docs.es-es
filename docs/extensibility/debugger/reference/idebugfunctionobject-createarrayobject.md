---
title: "IDebugFunctionObject::CreateArrayObject | Microsoft Docs"
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
  - "IDebugFunctionObject::CreateArrayObject"
helpviewer_keywords: 
  - "IDebugFunctionObject::CreateArrayObject (método)"
ms.assetid: a380e53c-15f1-401f-927f-f366eea789e6
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugFunctionObject::CreateArrayObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Crea un objeto array.  Esta matriz puede contener valores de primitivo o la instancia de objeto.  
  
## Sintaxis  
  
```cpp#  
HRESULT CreateArrayObject(   
   OBJECT_TYPE    ot,  
   IDebugField*   pClassField,  
   DWORD          dwRank,  
   DWORD          dwDims[],  
   DWORD          dwLowBounds[],  
   IDebugObject** ppObject  
);  
```  
  
```c#  
int CreateArrayObject(  
   enum_OBJECT_TYPE ot,   
   IDebugField      pClassField,   
   uint             dwRank,   
   uint[]           dwDims,   
   uint[]           dwLowBounds,   
   out IDebugObject ppObject  
);  
```  
  
#### Parámetros  
 `ot`  
 \[in\]  Especifica un valor de enumeración de [OBJECT\_TYPE](../../../extensibility/debugger/reference/object-type.md) que indica el tipo de objeto array.  
  
 `pClassField`  
 \[in\]  Un objeto de [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que representa la clase de un objeto, si crea una matriz de valores de la instancia de objeto.  Si crea una matriz de objetos primitivos, este parámetro es un valor null.  
  
 `dwRank`  
 \[in\]  La fila o el número de dimensiones de la matriz.  
  
 `dwDims`  
 \[in\]  Los tamaños de cada dimensión de la matriz.  
  
 `dwLowBounds`  
 \[in\]  El origen de cada dimensión \(normalmente 0 o 1\).  
  
 `ppObject`  
 \[out\]  Devuelve un objeto de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa la matriz creada recientemente.  esto es realmente un objeto de [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) .  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve S\_OK; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Llame a este método para crear un objeto que representa un parámetro de matriz a la función representada por la interfaz de [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .  
  
## Vea también  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)