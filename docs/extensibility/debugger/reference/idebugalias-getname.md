---
title: "IDebugAlias::GetName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugAlias::GetName"
helpviewer_keywords: 
  - "IDebugAlias::GetName (método)"
ms.assetid: ac2d8891-56b5-40ef-9866-ed74f18bb043
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugAlias::GetName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

obtiene el nombre de este alias.  
  
## Sintaxis  
  
```cpp  
HRESULT GetName(  
   BSTR* pbstrName  
);  
```  
  
```c#  
int GetName(  
   out string pbstrName  
);  
```  
  
#### Parámetros  
 `pbstrName`  
 \[out\]  Nombre del alias.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve S\_OK; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)