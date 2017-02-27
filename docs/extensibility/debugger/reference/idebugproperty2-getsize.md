---
title: "IDebugProperty2::GetSize | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty2::GetSize"
helpviewer_keywords: 
  - "IDebugProperty2::GetSize"
ms.assetid: 0deb8ec5-d6fb-4622-bb14-0c46b9459cc6
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProperty2::GetSize
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene el tamaño, en bytes, del valor de propiedad.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetSize (   
   DWORD* pdwSize  
);  
```  
  
```c#  
int GetSize (   
   out uint pdwSize  
);  
```  
  
#### Parámetros  
 `pdwSize`  
 \[out\]  Devuelve el tamaño, en bytes, del valor de propiedad.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; si no devuelve un código de error.  Devuelve `S_GETSIZE_NO_SIZE` si no tiene un tamaño.  
  
## Vea también  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)