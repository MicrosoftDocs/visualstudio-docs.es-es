---
title: "IDebugPointerObject::Dereference | Microsoft Docs"
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
  - "IDebugPointerObject::Dereference"
helpviewer_keywords: 
  - "IDebugPointerObject::Dereference (método)"
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPointerObject::Dereference
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene el objeto informa a.  
  
## Sintaxis  
  
```cpp#  
HRESULT DeReference(   
   DWORD          dwIndex,  
   IDebugObject** ppObject  
);  
```  
  
```c#  
int Dereference(  
   uint             dwIndex,   
   out IDebugObject ppObject  
);  
```  
  
#### Parámetros  
 `dwIndex`  
 \[in\]  Un desplazamiento de byte simple desde el inicio del objeto que en.  
  
 `ppObject`  
 \[out\]  Devuelve un objeto de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa el objeto informa a, más desplazamiento, si existe.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve S\_OK; de lo contrario, devuelve un código de error.  Devuelve E\_FAIL si este objeto no indica a otro objeto.  
  
## Comentarios  
 El objeto informa a puede ser un tipo primitivo o un tipo más complejo como una clase o estructura.  
  
## Vea también  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)