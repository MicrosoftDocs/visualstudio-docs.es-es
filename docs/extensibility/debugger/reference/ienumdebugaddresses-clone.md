---
title: "IEnumDebugAddresses::Clone | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugAddresses::Clone"
helpviewer_keywords: 
  - "IEnumDebugAddresses::Clone (método)"
ms.assetid: 71189a00-34eb-4c71-b96e-8bd6e70c6966
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# IEnumDebugAddresses::Clone
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Este método devuelve una copia de la enumeración actual como un objeto independiente.  
  
## Sintaxis  
  
```cpp#  
HRESULT Clone(  
   IEnumDebugAddresses** ppEnum  
);  
```  
  
```c#  
int Clone(  
   out IEnumDebugAddresses ppEnum  
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
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)