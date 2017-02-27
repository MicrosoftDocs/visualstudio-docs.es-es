---
title: "IEnumDebugAddresses::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugAddresses::Skip"
helpviewer_keywords: 
  - "IEnumDebugAddresses::Skip (método)"
ms.assetid: ed9a8e71-30ef-414b-9da5-c9a2a251b84e
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IEnumDebugAddresses::Skip
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Este método omite sobre el número especificado de elementos.  
  
## Sintaxis  
  
```cpp#  
HRESULT Skip(  
   [in] ULONG celt  
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
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)