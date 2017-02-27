---
title: "IDebugCustomAttribute::GetParentField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCustomAttribute::GetParentField"
helpviewer_keywords: 
  - "IDebugCustomAttribute::GetParentField"
ms.assetid: bcdfdf37-bfcf-4988-a7b8-4c731d0af1b0
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugCustomAttribute::GetParentField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene el campo al que se asocia el atributo personalizado.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetParentField(   
   IDebugField** ppField  
);  
```  
  
```c#  
int GetParentField(  
   out IDebugField ppField  
);  
```  
  
#### Parámetros  
 `ppField`  
 \[out\]  Devuelve el objeto de [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que representa el campo al que se asocia el atributo personalizado.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve S\_OK; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Llame al método de [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) en el objeto devuelto de [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) para determinar qué tipo de campo es el elemento primario.  
  
## Vea también  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)