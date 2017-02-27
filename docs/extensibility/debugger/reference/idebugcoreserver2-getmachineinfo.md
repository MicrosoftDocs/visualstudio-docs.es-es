---
title: "IDebugCoreServer2::GetMachineInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCoreServer2::GetInfo"
helpviewer_keywords: 
  - "IDebugCoreServer2::GetInfo"
ms.assetid: 8fa1a1d3-9fcb-4fb3-bf4e-e7172ac08d77
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugCoreServer2::GetMachineInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera una descripción del equipo que el servidor principal se ejecuta.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetInfo(   
   MACHINE_INFO_FIELDS Fields,  
   MACHINE_INFO*       pMachineInfo  
);  
```  
  
```c#  
int GetInfo(   
   enum_ MACHINE_INFO_FIELDS  Fields,  
   MACHINE_INFO[]             pMachineInfo  
);  
```  
  
#### Parámetros  
 `Fields`  
 \[in\]  Una combinación de marcadores de enumeración de [MACHINE\_INFO\_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md) que especifican qué campos de `pMachineInfo` se deben completar.  
  
 `pMachineInfo`  
 \[in, out\]  Una estructura de [MACHINE\_INFO](../../../extensibility/debugger/reference/machine-info.md) se completa con una descripción del equipo.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [MACHINE\_INFO\_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)   
 [MACHINE\_INFO](../../../extensibility/debugger/reference/machine-info.md)