---
title: "IDebugEngineLaunch2::CanTerminateProcess | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngineLaunch2::CanTerminateProcess"
helpviewer_keywords: 
  - "IDebugEngineLaunch2::CanTerminateProcess"
ms.assetid: 7973454d-c957-4123-a0ee-80ebcdbbd2d1
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugEngineLaunch2::CanTerminateProcess
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Determina si el proceso puede ser finalizado.  
  
## Sintaxis  
  
```cpp#  
HRESULT CanTerminateProcess (   
   IDebugProcess2* pProcess  
);  
```  
  
```c#  
int CanTerminateProcess (   
   IDebugProcess2 pProcess  
);  
```  
  
#### Parámetros  
 `pProcess`  
 \[in\]  Un objeto de [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) que representa el proceso que se terminará.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; si no devuelve un código de error.  devuelve `S_FALSE` si el motor no puede finalizar el proceso, por ejemplo, porque se deniega el acceso.  
  
## Comentarios  
 Si este método devuelve `S_OK`, el método de [TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md) puede llamar para finalizar realmente el proceso.  
  
## Vea también  
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)