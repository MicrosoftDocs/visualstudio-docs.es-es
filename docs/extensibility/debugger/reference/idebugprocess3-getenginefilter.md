---
title: "IDebugProcess3::GetEngineFilter | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetEngineFilter"
  - "IDebugProcess3::GetEngineFilter"
ms.assetid: ccb7ecb0-f189-4e80-b5b2-221a095e01f5
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugProcess3::GetEngineFilter
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera una matriz de identificadores únicos para los motores disponibles de depuración.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetEngineFilter(  
   GUID_ARRAY *pEngineArray  
);  
```  
  
```c#  
public int GetEngineFilter(  
   out GUID_ARRAY[] pEngineArray  
);  
```  
  
#### Parámetros  
 `pEngineArray`  
 \[out\]  Referencia a una estructura que contiene identificadores únicos para los motores de depuración.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [GUID\_ARRAY](../../../extensibility/debugger/reference/guid-array.md)