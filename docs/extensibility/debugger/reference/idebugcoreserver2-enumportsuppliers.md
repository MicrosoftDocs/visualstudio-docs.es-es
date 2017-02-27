---
title: "IDebugCoreServer2::EnumPortSuppliers | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCoreServer2::EnumPortSuppliers"
helpviewer_keywords: 
  - "IDebugCoreServer2::EnumPortSuppliers"
ms.assetid: ce0c90e4-8e02-4b08-b558-7677fb2c88f7
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugCoreServer2::EnumPortSuppliers
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera una lista de todos los proveedores disponibles de puerto.  
  
## Sintaxis  
  
```cpp#  
HRESULT EnumPortSuppliers(  
   IEnumDebugPortSuppliers2** ppEnum  
);  
```  
  
```c#  
int EnumPortSuppliers(  
   out IEnumDebugPortSuppliers2 ppEnum  
);  
```  
  
#### Parámetros  
 `ppEnum`  
 \[out\]  Devuelve un objeto de [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) que contiene una lista de todos los proveedores de puerto.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)