---
title: "IDebugField::GetTypeInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugField::GetTypeInfo"
helpviewer_keywords: 
  - "IDebugField::GetTypeInfo (método)"
ms.assetid: bb5acfa3-04c3-4088-be84-9ff8926cd16f
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugField::GetTypeInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Este método obtiene la información de la independientes del tipo sobre el símbolo o el tipo.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetTypeInfo(   
   TYPE_INFO* pTypeInfo  
);  
```  
  
```c#  
int GetTypeInfo(  
   TYPE_INFO[] pTypeInfo  
);  
```  
  
#### Parámetros  
 `pTypeInfo`  
 \[out\]  Devuelve información de tipo en la estructura proporcionada de [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md) .  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 la información de la independientes del tipo incluiría, por ejemplo, AppDomain, el módulo, y la clase que contiene el símbolo.  
  
## Vea también  
 [GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md)