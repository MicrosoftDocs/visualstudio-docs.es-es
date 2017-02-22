---
title: "IDebugObject::IsNullReference | Microsoft Docs"
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
  - "IDebugObject::IsNullReference"
helpviewer_keywords: 
  - "IDebugObject::IsNullReference (método)"
ms.assetid: 6dbfcdb0-954f-4486-8fac-7ea8d003e3a9
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugObject::IsNullReference
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Comprueba si este objeto es una referencia nula.  
  
## Sintaxis  
  
```cpp#  
HRESULT IsNullReference(   
   BOOL* pfIsNull  
);  
```  
  
```c#  
int IsNullReference(  
   out int pfIsNull  
);  
```  
  
#### Parámetros  
 `pfIsNull`  
 \[out\]  Devuelve cero \(`TRUE`\) si este objeto es una referencia nula; de lo contrario, devuelve cero \(`FALSE`\).  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve S\_OK; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Una referencia nula significa un objeto vacío o un objeto a los que no se ha asignado.  
  
## Vea también  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)