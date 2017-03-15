---
title: "IDebugBinder::ResolveRuntimeType | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBinder::ResolveRuntimeType"
helpviewer_keywords: 
  - "IDebugBinder::ResolveRuntimeType (método)"
ms.assetid: 6456ab3e-1c03-4f3c-91f9-16797ab7f5e7
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugBinder::ResolveRuntimeType
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Este método determina el tipo en tiempo de ejecución de un objeto.  
  
## Sintaxis  
  
```cpp#  
HRESULT ResolveRuntimeType(   
   IDebugObject* pObject,  
   IDebugField** ppResolved  
);  
```  
  
```c#  
int ResolveRuntimeType(  
   IDebugObject     pObject,   
   out IDebugField  ppResolved  
);  
```  
  
#### Parámetros  
 `pObject`  
 \[in\]  [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que se resolverá.  
  
 `ppResolved`  
 \[out\]  Devuelve el tipo de objeto como [IDebugField](../../../extensibility/debugger/reference/idebugfield.md).  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 No se conoce el tipo en tiempo de ejecución de un objeto siempre en tiempo de compilación.  Por ejemplo, utilizando el polimorfismo, un argumento se puede pasar a una función como clase base, como una clase button.  El argumento real podría ser una clase derivada, como una clase de botón de radio.  
  
## Vea también  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)