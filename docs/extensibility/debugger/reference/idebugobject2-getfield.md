---
title: "IDebugObject2::GetField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject2::GetField"
helpviewer_keywords: 
  - "IDebugObject2::GetField (método)"
ms.assetid: add6a6b5-e752-47dd-9613-29206ea809b0
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugObject2::GetField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

obtiene el tipo de este objeto.  
  
## Sintaxis  
  
```cpp  
HRESULT GetField(  
 IDebugField** ppField  
);  
```  
  
```c#  
int GetField(  
   out IDebugField ppField  
);  
```  
  
#### Parámetros  
 `ppField`  
 \[out\]  Devuelve un objeto de [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) si no es un valor null.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve S\_OK; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Un campo describe el tipo de objeto.  
  
## Vea también  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)