---
title: "IEnumDebugPropertyInfo2::Clone | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugPropertyInfo2::Clone"
helpviewer_keywords: 
  - "IEnumDebugPropertyInfo2::Clone"
ms.assetid: 0ede1667-1071-4aa4-b887-260ea103d724
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEnumDebugPropertyInfo2::Clone
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Devuelve una copia de la enumeración actual como un objeto independiente.  
  
## Sintaxis  
  
```cpp#  
HRESULT Clone(  
   IEnumDebugPropertyInfo2** ppEnum  
);  
```  
  
```c#  
int Clone(  
   out IEnumDebugPropertyInfo2 ppEnum  
);  
```  
  
#### Parámetros  
 `ppEnum`  
 \[out\]  Devuelve una copia de esta enumeración como un objeto independiente.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 La copia de la enumeración tiene el mismo estado que el original cuando se llama a este método.  Sin embargo, la copia y estados original son independientes y se pueden cambiar individualmente.  
  
## Vea también  
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)