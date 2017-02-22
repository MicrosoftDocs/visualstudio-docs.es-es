---
title: "IDebugPointerObject::SetBytes | Microsoft Docs"
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
  - "IDebugPointerObject::SetBytes"
helpviewer_keywords: 
  - "IDebugPointerObject::SetBytes (método)"
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPointerObject::SetBytes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Establece el valor indicado de una serie de bytes consecutivos.  
  
## Sintaxis  
  
```cpp#  
HRESULT SetBytes(   
   DWORD  dwStart,  
   DWORD  dwCount,  
   BYTE*  pBytes,  
   DWORD* pdwBytes  
);  
```  
  
```c#  
int SetBytes(  
   uint     dwStart,   
   uint     dwCount,   
   byte[]   pBytes,   
   out uint pdwBytes  
);  
```  
  
#### Parámetros  
 `dwStart`  
 \[in\]  Una diferencia, en bytes, desde el inicio del objeto que en.  
  
 `dwCount`  
 \[in\]  El número de bytes al conjunto.  
  
 `pBytes`  
 \[in\]  Una matriz de byte que representa el nuevo valor.  Este valor se almacena en el objeto, comenzando en el desplazamiento especificado.  
  
 `pdwBytes`  
 \[out\]  devuelve el número de bytes establecidos realmente.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve S\_OK; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Este método se utiliza si el puntero como se representa por este puntos de [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) a un tipo primitivo o a una matriz simple de los tipos primitivos \(es decir, una matriz que se puede representar mediante una secuencia de bytes simple\).  este objeto de `IDebugPointerObject` no puede ser una referencia nula \(debe señalar a una dirección en memoria\).  
  
## Vea también  
 [GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)   
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)