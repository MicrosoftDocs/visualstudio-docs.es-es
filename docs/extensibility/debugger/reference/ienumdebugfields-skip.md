---
title: "IEnumDebugFields::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugFields::Skip"
helpviewer_keywords: 
  - "IEnumDebugFields::Skip (método)"
ms.assetid: b3bc51c4-21ae-4913-800c-c2ca9dc18443
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IEnumDebugFields::Skip
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Este método omite sobre el número especificado de elementos.  
  
## Sintaxis  
  
```cpp#  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
```c#  
int Skip(  
   uint celt  
);  
```  
  
#### Parámetros  
 `celt`  
 \[in\]  Número de elementos que se van a omitir.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`.  devuelve `S_FALSE` si `celt` es mayor que el número de elementos restantes; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Si `celt` especifica un valor mayor que el número de elementos restantes, la enumeración se establece al final y se devuelve `S_FALSE` .  
  
## Vea también  
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)