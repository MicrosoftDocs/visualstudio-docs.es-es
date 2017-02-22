---
title: "IDebugArrayObject::GetDimensions | Microsoft Docs"
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
  - "IDebugArrayObject::GetDimensions"
helpviewer_keywords: 
  - "IDebugArrayObject::GetDimensions (método)"
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugArrayObject::GetDimensions
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene las dimensiones de la matriz.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetDimensions(   
   DWORD dwCount,  
   DWORD dwDimensions[]  
);  
```  
  
```c#  
int GetDimensions(  
   [In] uint    dwCount,   
   [Out] uint[] dwDimensions  
);  
```  
  
#### Parámetros  
 `dwCount`  
 \[in\]  el número de dimensiones a recuperar.  
  
 `dwDimensions`  
 \[in, out\]  Una matriz que se completa con los tamaños de cada dimensión.  `dwCount` especifica el tamaño máximo de la matriz de `dwDimensions` .  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve S\_OK; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Una matriz multidimensional puede tener distintos tamaños para cada dimensión.  Por ejemplo, dada la matriz tridimensional `myarray[3][2][6]`, este método devolverá 3, 2 y 6, en el parámetro de `dwDimensions` en ese orden.  
  
## Vea también  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)