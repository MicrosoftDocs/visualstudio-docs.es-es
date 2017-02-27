---
title: "IDebugPortSupplier2::GetPortSupplierId | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortSupplier2::GetPortSupplierId"
helpviewer_keywords: 
  - "IDebugPortSupplier2::GetPortSupplierId"
ms.assetid: 741d0829-0943-49bf-b56e-61e836043006
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPortSupplier2::GetPortSupplierId
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene el identificador del proveedor de puerto.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetPortSupplierId(   
   GUID* pguidPortSupplier  
);  
```  
  
```c#  
HRESULT GetPortSupplierId(   
   out Guid pguidPortSupplier  
);  
```  
  
#### Parámetros  
 `pguidPortSupplier`  
 \[out\]  Devuelve el GUID del proveedor de puerto.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)