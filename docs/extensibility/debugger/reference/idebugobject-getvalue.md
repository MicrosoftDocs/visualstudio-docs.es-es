---
title: "IDebugObject::GetValue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject::GetValue"
helpviewer_keywords: 
  - "IDebugObject::GetValue (método)"
ms.assetid: eec6051e-8ecb-49fa-bdd4-dd786f211692
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugObject::GetValue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene el valor del objeto como serie consecutiva de bytes.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetValue(   
   BYTE* pValue,  
   UINT  nSize  
);  
```  
  
```c#  
int GetValue(  
   ref byte[] pValue,   
   uint nSize  
);  
```  
  
#### Parámetros  
 `pValue`  
 \[in, out\]  Una matriz que se rellena con una ejecución consecutiva de byte que representa el valor del objeto.  
  
 `nSize`  
 \[in\]  el número de bytes máximo a capturar.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve S\_OK; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Obtiene el número total de bytes de valores que pueden ser capturados llamando al método de [GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md) .  
  
## Vea también  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)