---
title: "IDebugArrayObject::GetElement | Microsoft Docs"
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
  - "IDebugArrayObject::GetElement"
helpviewer_keywords: 
  - "IDebugArrayObject::GetElement (método)"
ms.assetid: 08b44341-7bf1-4a8c-8b79-98ae5785b195
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugArrayObject::GetElement
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene un elemento de la matriz.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetElement(   
   DWORD          dwIndex,  
   IDebugObject** ppElement  
);  
```  
  
```c#  
int GetElement(  
   [In] uint dwIndex,   
   out IDebugObject ppElement  
);  
```  
  
#### Parámetros  
 `dwIndex`  
 \[in\]  El índice del elemento.  
  
 `ppElement`  
 \[out\]  Devuelve una interfaz de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa el elemento.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve S\_OK; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Este método considera todos los elementos de un objeto de matriz una matriz unidimensional, aunque el objeto array es multidimensional.  Por ejemplo, dada la matriz `myarray[3][2][6]` y un parámetro de `dwIndex` de 20, este método devolverá el elemento de `myarray[1][1][2]`, y un parámetro de `dwIndex` de 21 devolverá el elemento de `myarray[1][1][3]`.  Utilice el método de [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) para determinar el número total de elementos de la matriz.  
  
## Vea también  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)