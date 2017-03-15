---
title: "IDebugArrayObject::GetCount | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugArrayObject::GetCount"
helpviewer_keywords: 
  - "IDebugArrayObject::GetCount (método)"
ms.assetid: 7931f3f7-033c-4bf8-8abd-95183952ebb0
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugArrayObject::GetCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene el número de elementos de la matriz.  
  
## Sintaxis  
  
```  
[C++]  
HRESULT GetCount(   
   DWORD* pdwElements  
);  
```  
  
```  
[C#]  
int GetCount(  
   out uint pdwElements  
);  
```  
  
#### Parámetros  
 `pdwElements`  
 \[out\]  devuelve el recuento.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve S\_OK; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Este método considera todos los elementos de un objeto de matriz una matriz unidimensional, aunque el objeto array es multidimensional.  Por ejemplo, dada la matriz `myarray[3][2][6]`, este método devolverá 36 en el parámetro de `pdwElements` .  Utilice el método de [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) para recuperar los elementos individuales de una en una.  
  
## Vea también  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)