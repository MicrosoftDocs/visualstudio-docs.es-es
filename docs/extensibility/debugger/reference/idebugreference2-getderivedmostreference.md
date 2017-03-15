---
title: "IDebugReference2::GetDerivedMostReference | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugReference2::GetDerivedMostReference"
helpviewer_keywords: 
  - "IDebugReference2::GetDerivedMostReference"
ms.assetid: 07253b74-7d39-48e0-8e85-ac8dfd919f6e
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugReference2::GetDerivedMostReference
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

obtiene la referencia derivada\-más de una referencia.  Reservado para un uso futuro.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetDerivedMostReference(   
   IDebugReference2** ppDerivedMost  
);  
```  
  
```c#  
int GetDerivedMostReference(   
   out IDebugReference2 ppDerivedMost  
);  
```  
  
#### Parámetros  
 `ppDerivedMost`  
 \[out\]  Devuelve un objeto de [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) que representa la propiedad derivada\-más.  
  
## Valor devuelto  
 Siempre devuelve `E_NOTIMPL`.  
  
## Comentarios  
 Por ejemplo, si esta propiedad describe un objeto que implementa `ClassRoot` pero que en realidad es una instancia de `ClassDerived` que es derivada de `ClassRoot`, este método devuelve un objeto de [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) que representa una referencia al objeto de `ClassDerived` .  
  
## Vea también  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)