---
title: "IEnumDebugFields::Clone | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugFields::Clone"
helpviewer_keywords: 
  - "IEnumDebugFields::Clone (método)"
ms.assetid: 7ec265a8-696f-45ce-a2a2-0a83e96fee1b
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# IEnumDebugFields::Clone
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Este método devuelve una copia de la enumeración actual como un objeto independiente.  
  
## Sintaxis  
  
```cpp#  
HRESULT Clone(  
   IEnumDebugFields** ppEnum  
);  
```  
  
```c#  
int Clone(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### Parámetros  
 `ppEnum`  
 \[out\]  Devuelve una copia de esta enumeración como un objeto independiente.  
  
## Valor de propiedad y valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 La copia de la enumeración tiene el mismo estado que el original cuando se llama a este método.  Sin embargo, la copia y estados original son independientes y se pueden cambiar individualmente.  
  
## Vea también  
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)