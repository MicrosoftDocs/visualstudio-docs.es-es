---
title: "IDebugObject::IsEqual | Microsoft Docs"
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
  - "IDebugObject::IsEqual"
helpviewer_keywords: 
  - "IDebugObject::IsEqual (método)"
ms.assetid: 4b76e663-ef2e-41ff-9be1-bf26d666a34a
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugObject::IsEqual
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

compara un objeto con este objeto.  
  
## Sintaxis  
  
```cpp#  
HRESULT IsEqual(   
   IDebugObject* pObject,  
   BOOL*         pfIsEqual  
);  
```  
  
```c#  
int IsEqual(  
   IDebugObject pObject,  
   out int      pfIsEqual  
);  
```  
  
#### Parámetros  
 `pObject`  
 \[in\]  Un objeto de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa el objeto que se va a comparar.  
  
 `pfIsEqual`  
 \[out\]  Devuelve cero \(`TRUE`\) si los valores de los objetos son iguales; de lo contrario, devuelve cero \(`FALSE`\).  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve S\_OK; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Normalmente, este método puede comparar las direcciones de los valores representados por el parámetro de `pObject` y este objeto de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) ; si las direcciones son iguales, los objetos se pueden considerarse iguales.  
  
## Vea también  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)