---
title: "IDebugProperty2::GetDerivedMostProperty | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty2::GetDerivedMostProperty"
helpviewer_keywords: 
  - "IDebugProperty2::GetDerivedMostProperty"
ms.assetid: cc86b461-62d1-4340-8209-c65037fd8b02
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugProperty2::GetDerivedMostProperty
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

obtiene la propiedad derivada\-más de una propiedad.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetDerivedMostProperty (   
   IDebugProperty2** ppDerivedMost  
);  
```  
  
```c#  
int GetDerivedMostProperty (   
   out IDebugProperty2 ppDerivedMost  
);  
```  
  
#### Parámetros  
 `ppDerivedMost`  
 \[out\]  Devuelve un objeto de [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) que representa la propiedad derivada\-más.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; si no devuelve un código de error.  Devuelve `S_GETDERIVEDMOST_NO_DERIVED_MOST` si no hay ninguna propiedad derivada\-más a recuperar.  
  
## Comentarios  
 Por ejemplo, si esta propiedad describe un objeto que implementa `ClassRoot` pero que en realidad es una instancia de `ClassDerived` que es derivada de `ClassRoot`, este método devuelve un objeto de [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) que describe el objeto de `ClassDerived` .  
  
## Vea también  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)