---
title: "IDebugObject::SetValue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject::SetValue"
helpviewer_keywords: 
  - "IDebugObject::SetValue (método)"
ms.assetid: d652e09c-cdc1-4519-8116-d7c743f5679b
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugObject::SetValue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Establece el valor de objeto de una serie consecutiva de bytes.  
  
## Sintaxis  
  
```cpp#  
HRESULT SetValue(   
   BYTE* pValue,  
   UINT  nSize  
);  
```  
  
```c#  
int SetValue(  
   byte[] pValue,   
   uint   nSize  
);  
```  
  
#### Parámetros  
 `pValue`  
 \[in\]  Una matriz de byte que representa el nuevo valor.  
  
 `nSize`  
 \[in\]  El tamaño del valor en bytes.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve S\_OK; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Los valores de la matriz se copian en este objeto de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) , reemplazando los valores existentes.  El tamaño del nuevo valor puede ser mayor o menor que el valor existente.  este `IDebugObject` no puede ser una referencia nula.  
  
## Vea también  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)