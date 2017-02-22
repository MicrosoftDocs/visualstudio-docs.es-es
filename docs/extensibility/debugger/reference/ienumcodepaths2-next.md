---
title: "IEnumCodePaths2::Next | Microsoft Docs"
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
  - "IEnumCodePaths2::Next"
helpviewer_keywords: 
  - "IEnumCodePaths2::Next"
ms.assetid: c7a8fe97-2abc-4cee-8aef-64f1daa93b5c
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumCodePaths2::Next
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Devuelve el conjunto de elementos de la enumeración.  
  
## Sintaxis  
  
```cpp#  
HRESULT Next(  
   ULONG       celt,  
   CODE_PATH** rgelt,  
   ULONG*      pceltFetched  
);  
```  
  
```c#  
int Next(  
   uint        celt,  
   CODE_PATH[] rgelt,  
   ref uint    pceltFetched  
);  
```  
  
#### Parámetros  
 `celt`  
 \[in\]  Número de elementos que se van a recuperar.  También especifica el tamaño máximo de la matriz de `rgelt` .  
  
 `rgelt`  
 \[in, out\]  Matriz de elementos de [CODE\_PATH](../../../extensibility/debugger/reference/code-path.md) que se completan.  
  
 `pceltFetched`  
 \[out\]  devuelve el número de elementos devueltos realmente en `rgelt`.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`.  Devuelve `S_FALSE` si menor que el número solicitado de elementos podrían devolverse; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)   
 [CODE\_PATH](../../../extensibility/debugger/reference/code-path.md)