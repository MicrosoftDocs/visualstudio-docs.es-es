---
title: "IEnumDebugReferenceInfo2::Next | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugReferenceInfo2::Next"
helpviewer_keywords: 
  - "IEnumDebugReferenceInfo2::Next"
ms.assetid: 70b31a57-1701-4757-9e7e-63ec60a71b3c
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEnumDebugReferenceInfo2::Next
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Devuelve el conjunto de elementos de la enumeración.  
  
## Sintaxis  
  
```cpp#  
HRESULT Next(  
   ULONG                   celt,  
   DEBUG_REFERENCE_INFO ** rgelt,  
   ULONG*                  pceltFetched  
);  
```  
  
```c#  
int Next(  
   uint                   celt,  
   DEBUG_REFERENCE_INFO[] rgelt,  
   ref uint               pceltFetched  
);  
```  
  
#### Parámetros  
 `celt`  
 \[in\]  Número de elementos que se van a recuperar.  También especifica el tamaño máximo de la matriz de `rgelt` .  
  
 `rgelt`  
 \[in, out\]  Matriz de elementos de [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) que se completan.  
  
 `pceltFetched`  
 \[out\]  devuelve el número de elementos devueltos realmente en `rgelt`.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`.  Devuelve `S_FALSE` si menor que el número solicitado de elementos podrían devolverse; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)   
 [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)