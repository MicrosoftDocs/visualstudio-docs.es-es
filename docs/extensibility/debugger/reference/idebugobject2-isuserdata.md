---
title: "IDebugObject2::IsUserData | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject2::IsUserData"
helpviewer_keywords: 
  - "IDebugObject2::IsUserData (método)"
ms.assetid: 6ffa0d0e-f742-496d-acc7-db74c248bc45
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugObject2::IsUserData
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

determina si el objeto representa datos de usuario.  
  
## Sintaxis  
  
```cpp  
HRESULT IsUserData(  
   BOOL* pfUser  
);  
```  
  
```c#  
int IsUserData(  
   out int pfUser  
);  
```  
  
#### Parámetros  
 `pfUser`  
 \[out\]  Devuelve cero \(`TRUE`\) si el objeto representa datos de usuario; cero \(`FALSE`\) si no lo hace.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve S\_OK; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Los datos de usuario es cualquier objeto que forma parte de un módulo designado como JustMyCode \(una opción usuario\-configurable que marca un módulo como código de usuario y por consiguiente visible en el seguimiento de la pila\).  
  
## Vea también  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)