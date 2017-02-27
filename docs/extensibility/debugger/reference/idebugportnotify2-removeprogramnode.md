---
title: "IDebugPortNotify2::RemoveProgramNode | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortNotify2::RemoveProgramNode"
helpviewer_keywords: 
  - "IDebugPortNotify2::RemoveProgramNode"
ms.assetid: 3668157b-66d2-416e-a359-fc04dcd18a48
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPortNotify2::RemoveProgramNode
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Anula que un programa que se puede depurar el puerto se está ejecutando.  
  
## Sintaxis  
  
```cpp#  
HRESULT RemoveProgramNode(   
   IDebugProgramNode2* pProgramNode  
);  
```  
  
```c#  
int RemoveProgramNode(   
   IDebugProgramNode2 pProgramNode  
);  
```  
  
#### Parámetros  
 `pProgramNode`  
 \[in\]  Un objecy de [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) que representa el programa no esté registrado.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Este método quita un nodo del programa que se agregó con una llamada al método de [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) .  
  
## Vea también  
 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)