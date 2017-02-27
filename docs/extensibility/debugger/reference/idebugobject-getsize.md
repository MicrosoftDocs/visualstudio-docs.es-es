---
title: "IDebugObject::GetSize | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject::GetSize"
helpviewer_keywords: 
  - "IDebugObject::GetSize (método)"
ms.assetid: 89af423b-36eb-479d-b2de-2693455eca15
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugObject::GetSize
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene el tamaño en bytes.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetSize(   
   UINT* pnSize  
);  
```  
  
```c#  
int GetSize(  
   out uint pnSize  
);  
```  
  
#### Parámetros  
 `pnSize`  
 \[out\]  Devuelve el tamaño en bytes.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve S\_OK; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Utilice el método de [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md) para recuperar el valor como una secuencia de bytes.  
  
## Vea también  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)