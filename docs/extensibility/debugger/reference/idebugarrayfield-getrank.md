---
title: "IDebugArrayField::GetRank | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugArrayField::GetRank"
helpviewer_keywords: 
  - "IDebugArrayField::GetRank (método)"
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugArrayField::GetRank
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene la fila o el número de dimensiones de la matriz.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetRank(   
   DWORD* pdwRank  
);  
```  
  
```c#  
int GetRank(  
   out uint pdwRank  
);  
```  
  
#### Parámetros  
 `pdwRank`  
 \[out\]  devuelve a la fila.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve S\_OK; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 La fila de una matriz corresponde al número de dimensiones.  En C\+\+ y C\#, las matrices multidimensionales son realmente matrices de matrices y pueden por consiguiente ver solamente una matriz unidimensional \(y el método de `GetRank` siempre devuelve 1\).  En [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)], por otra parte, las matrices multidimensionales se controlan de manera diferente y fila de este tipo de matriz refleja el número de dimensiones \(y método de `GetRank` siempre devuelve el número de dimensiones\).  
  
## Vea también  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)