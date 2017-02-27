---
title: "IDebugPort2::EnumProcesses | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPort2::EnumProcesses"
helpviewer_keywords: 
  - "IDebugPort2::EnumProcesses"
ms.assetid: aafb32c5-5790-4807-a448-878a80256438
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPort2::EnumProcesses
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

devuelve una lista de todos los procesos que se ejecutan en un puerto.  
  
## Sintaxis  
  
```cpp#  
HRESULT EnumProcesses(   
   IEnumDebugProcesses2** ppEnum  
);  
```  
  
```c#  
int EnumProcesses(   
   out IEnumDebugProcesses2 ppEnum  
);  
```  
  
#### Parámetros  
 `ppEnum`  
 \[out\]  Devuelve un objeto de [IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md) que contiene una lista de todos los procesos que se ejecutan en un puerto.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)