---
title: "IDebugArrayObject2::GetBaseIndices | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetBaseIndices"
  - "IDebugArrayObject2::GetBaseIndices"
ms.assetid: 882951a2-3da0-49bf-8d1e-7daedd13ffe6
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugArrayObject2::GetBaseIndices
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera los índices bases \(límites inferior\) para cada índice especificado el número de dimensiones de la matriz.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetBaseIndices (  
   DWORD  dwRank,  
   DWORD* dwIndices  
);  
```  
  
```c#  
int GetBaseIndices (  
   uint       dwRank,  
   out uint[] dwIndices  
);  
```  
  
#### Parámetros  
 `dwRank`  
 \[in\]  El número de dimensiones \(fila\) de la matriz.  
  
 `dwIndices`  
 \[out\]  Los índices bases \(límites inferior\) para la matriz.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Como ejemplo, esta función devuelve “5 " para la matriz creada por el siguiente código de C\#:  
  
```  
int[] lengths = { 12 };  
int[] lowerbounds = { 5 };  
Array.CreateInstance(typeof(int), lengths, lowerbounds);  
```  
  
## Vea también  
 [IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)