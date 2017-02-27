---
title: "IDebugPortEx2::GetPortProcessId | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortEx2::GetPortProcessId"
helpviewer_keywords: 
  - "IDebugPortEx2::GetPortProcessId"
ms.assetid: be85be66-47e6-415f-b0ca-24599aa5f13c
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPortEx2::GetPortProcessId
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene el identificador de proceso de puerto propio.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetPortProcessId (   
   DWORD* pdwProcessId  
);  
```  
  
```c#  
int GetPortProcessId (   
   out uint pdwProcessId  
);  
```  
  
#### Parámetros  
 `pdwProcessId`  
 \[out\]  Devuelve el identificador de proceso físico de puerto propio.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 En tiempo de ejecución de Win32 como, este método llama normalmente la función `GetCurrentProcessId` Win32 para obtener el identificador de proceso físico  
  
## Vea también  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)