---
title: "IDebugPointerObject::GetBytes | Microsoft Docs"
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
  - "IDebugPointerObject::GetBytes"
helpviewer_keywords: 
  - "IDebugPointerObject::GetBytes (método)"
ms.assetid: e986c188-87fb-4b51-86e9-ee6a0035bdab
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPointerObject::GetBytes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene el valor designado como una serie de bytes consecutivos.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetBytes(   
   DWORD  dwStart,  
   DWORD  dwCount,  
   BYTE*  pBytes,  
   DWORD* pdwBytes  
);  
```  
  
```c#  
int GetBytes(  
   uint       dwStart,   
   uint       dwCount,   
   out byte[] pBytes,   
   out uint   pdwBytes  
);  
```  
  
#### Parámetros  
 `dwStart`  
 \[in\]  Una diferencia, en bytes, desde el inicio del objeto que en.  
  
 `dwCount`  
 \[in\]  el número de bytes a recuperar.  
  
 `pBytes`  
 \[in, out\]  Una matriz que se completa con el valor como una serie de bytes consecutivos, comenzando en el desplazamiento especificado del objeto que en.  
  
 `pdwBytes`  
 \[out\]  devuelve el número de bytes recuperados realmente.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve S\_OK; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Este método se utiliza si el puntero como se representa por este puntos de [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) a un tipo primitivo o a una matriz simple de los tipos primitivos \(es decir, una matriz que se puede representar mediante una secuencia de bytes simple\).  
  
## Vea también  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)   
 [SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)