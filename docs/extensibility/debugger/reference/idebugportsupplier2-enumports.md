---
title: "IDebugPortSupplier2::EnumPorts | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortSupplier2::EnumPorts"
helpviewer_keywords: 
  - "IDebugPortSupplier2::EnumPorts"
ms.assetid: 88b57fd2-eba1-44fa-bd34-cf2ad2b1ff87
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPortSupplier2::EnumPorts
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera una lista de todos los puertos proporcionados por un proveedor de puerto.  
  
## Sintaxis  
  
```cpp#  
HRESULT EnumPorts(   
   IEnumDebugPorts2** ppEnum  
);  
```  
  
```c#  
int EnumPorts(   
   out IEnumDebugPorts2 ppEnum  
);  
```  
  
#### Parámetros  
 `ppEnum`  
 \[out\]  devuelve un objeto de [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) que contiene una lista de puertos proporcionados.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)