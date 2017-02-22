---
title: "IDebugArrayObject::GetElements | Microsoft Docs"
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
  - "IDebugArrayObject::GetElements"
helpviewer_keywords: 
  - "IDebugArrayObject::GetElements (método)"
ms.assetid: f6a6262f-5183-46ce-8a45-33ef46088b98
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugArrayObject::GetElements
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene un enumerador de todos los elementos de la matriz.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetElements(   
   IEnumDebugObjects** ppEnum  
);  
```  
  
```c#  
int GetElements(  
   out IEnumDebugObjects ppEnum  
);  
```  
  
#### Parámetros  
 `ppEnum`  
 \[out\]  Devuelve un objeto de [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md) que permita el enumerar todos los elementos.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve S\_OK; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Como alternativa, use los métodos de [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) y de [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) para recorrer en iteración los elementos.  
  
## Vea también  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)