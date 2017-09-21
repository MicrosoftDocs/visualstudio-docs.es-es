---
title: "IDebugCoreServer2::GetMachineName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCoreServer2::GetName"
helpviewer_keywords: 
  - "IDebugCoreServer2::GetName"
ms.assetid: 693bd794-7215-4f07-8651-b57366d39953
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugCoreServer2::GetMachineName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene el nombre del equipo que el servidor principal se ejecuta.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetName(   
   BSTR* pbstrName  
);  
```  
  
```c#  
int GetName(   
   out string pbstrName  
);  
```  
  
#### Parámetros  
 `pbstrName`  
 \[out\]  Devuelve una cadena que contiene el nombre del equipo.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)