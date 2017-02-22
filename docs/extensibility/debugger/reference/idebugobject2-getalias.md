---
title: "IDebugObject2::GetAlias | Microsoft Docs"
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
  - "IDebugObject2::GetAlias"
helpviewer_keywords: 
  - "IDebugObject2::GetAlias (método)"
ms.assetid: aa6824d5-c932-42ba-8713-950e7d1fb42f
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugObject2::GetAlias
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene el alias asociado a este objeto, si existe.  
  
## Sintaxis  
  
```cpp  
HRESULT GetAlias(  
   IDebugAlias** ppAlias  
);  
```  
  
```c#  
int GetAlias(  
   out IDebugAlias ppAlias  
);  
```  
  
#### Parámetros  
 `ppAlias`  
 \[out\]  Devuelve un objeto de [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) que representa un alias para este objeto; de lo contrario, devuelve un valor null.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve S\_OK; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 El alias de un objeto se crea con una llamada al método de [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) .  
  
## Vea también  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)