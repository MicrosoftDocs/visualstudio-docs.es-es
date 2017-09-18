---
title: "IEnumCodePaths2::Clone | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumCodePaths2::Clone"
helpviewer_keywords: 
  - "IEnumCodePaths2::Clone"
ms.assetid: 9d5c6bc6-7e72-4f1b-801c-7192458f3ba8
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEnumCodePaths2::Clone
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Devuelve una copia de la enumeración actual como un objeto independiente.  
  
## Sintaxis  
  
```cpp#  
HRESULT Clone(  
   IEnumCodePaths2** ppEnum  
);  
```  
  
```c#  
int Clone(  
   out IEnumCodePaths2 ppEnum  
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
 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)