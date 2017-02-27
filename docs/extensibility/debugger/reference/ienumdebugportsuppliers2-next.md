---
title: "IEnumDebugPortSuppliers2::Next | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugPortSuppliers2::Next"
helpviewer_keywords: 
  - "IEnumDebugPortSuppliers2::Next"
ms.assetid: e2a2d226-e70b-42c2-bf00-a936517940c8
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IEnumDebugPortSuppliers2::Next
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Devuelve el conjunto de elementos de la enumeración.  
  
## Sintaxis  
  
```cpp#  
HRESULT Next(  
   ULONG                 celt,  
   IDebugPortSupplier2** rgelt,  
   ULONG*                pceltFetched  
);  
```  
  
```c#  
int Next(  
   uint                  celt,  
   IDebugPortSupplier2[] rgelt,  
   ref uint              pceltFetched  
);  
```  
  
#### Parámetros  
 `celt`  
 \[in\]  Número de elementos que se van a recuperar.  También especifica el tamaño máximo de la matriz de `rgelt` .  
  
 `rgelt`  
 \[in, out\]  Matriz de elementos de [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) que se completan.  
  
 `pceltFetched`  
 \[out\]  devuelve el número de elementos devueltos realmente en `rgelt`.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`.  Devuelve `S_FALSE` si menor que el número solicitado de elementos podrían devolverse; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)