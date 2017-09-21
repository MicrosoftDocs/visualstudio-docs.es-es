---
title: "IDebugBinder3::GetTypeArgumentCount | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBinder3::GetTypeArgumentCount"
helpviewer_keywords: 
  - "IDebugBinder3::GetTypeArgumentCount (método)"
ms.assetid: caf68de6-6f7c-4efd-b803-121347a5032e
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugBinder3::GetTypeArgumentCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Este método devuelve el número de tipos de argumento asociado a este objeto.  
  
## Sintaxis  
  
```cpp  
HRESULT GetTypeArgumentCount(  
   UINT* uCount  
);  
```  
  
```c#  
int GetTypeArgumentCount(  
   out uint uCount  
);  
```  
  
#### Parámetros  
 `uCount`  
 \[out\]  Número de tipos de argumento asociado a este objeto.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 El valor devuelto por este método se puede usar para asignar una matriz con el método de [GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md) .  
  
## Vea también  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)