---
title: "IDebugModule3::IsUserCode | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugModule3::IsUserCode"
helpviewer_keywords: 
  - "IDebugModule3::IsUserCode"
ms.assetid: 77022946-bb8b-4114-aa81-614df6e54b13
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugModule3::IsUserCode
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera información de si el módulo representa el código de usuario o no.  
  
## Sintaxis  
  
```cpp#  
HRESULT IsUserCode(  
   BOOL* pfUser  
);  
```  
  
```c#  
int IsUserCode(  
   out int pfUser  
);  
```  
  
#### Parámetros  
 `pfUser`  
 \[out\]  Cero \(`TRUE`\) si el módulo representa el código de usuario, cero \(`FALSE`\) si no lo hace.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve el código de error.  
  
## Vea también  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)