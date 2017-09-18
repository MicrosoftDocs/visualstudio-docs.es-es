---
title: "IEnumDebugObjects::Next | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugObjects::Next"
helpviewer_keywords: 
  - "IEnumDebugObjects::Next (método)"
ms.assetid: e54c3055-6030-4dc9-9f7a-5e3ce75f252f
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IEnumDebugObjects::Next
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Este método devuelve el siguiente conjunto de elementos de la enumeración.  
  
## Sintaxis  
  
```cpp#  
HRESULT Next(  
   ULONG          celt,  
   IDebugObject** rgelt,  
   ULONG*         pceltFetched  
);  
```  
  
```c#  
int Next(  
   uint           celt,  
   IDebugObject[] rgelt,  
   ref uint       pceltFetched  
);  
```  
  
#### Parámetros  
 `celt`  
 \[in\]  Número de elementos que se van a recuperar.  También especifica el tamaño máximo de la matriz de `rgelt` .  
  
 `rgelt`  
 \[in, out\]  Matriz de elementos de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que se completan.  
  
 `pceltFetched`  
 \[out\]  devuelve el número de elementos devueltos realmente en `rgelt`.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`.  Devuelve `S_FALSE` si menor que el número solicitado de elementos podrían devolverse; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)