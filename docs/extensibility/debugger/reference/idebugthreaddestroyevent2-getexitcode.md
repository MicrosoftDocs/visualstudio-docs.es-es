---
title: "IDebugThreadDestroyEvent2::GetExitCode | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugThreadDestroyEvent2::GetExitCode"
helpviewer_keywords: 
  - "IDebugThreadDestroyEvent2::GetExitCode"
ms.assetid: 8bf47a17-f811-4d9b-bcea-7488908830ff
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugThreadDestroyEvent2::GetExitCode
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene el código de salida de un subproceso.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetExitCode (   
   DWORD* pdwExit  
);  
```  
  
```c#  
int GetExitCode (   
   out uint pdwExit  
);  
```  
  
#### Parámetros  
 `pdwExit`  
 \[out\]  Devuelve el código de salida del subproceso.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)