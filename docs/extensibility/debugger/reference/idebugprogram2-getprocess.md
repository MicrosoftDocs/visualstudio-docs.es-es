---
title: "IDebugProgram2::GetProcess | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::GetProcess"
helpviewer_keywords: 
  - "IDebugProgram2::GetProcess"
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugProgram2::GetProcess
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtenga el proceso que este programa ejecuta en.  
  
## Sintaxis  
  
```cpp  
HRESULT GetProcess(  
   IDebugProcess2** ppProcess  
);  
```  
  
```c#  
int GetProcess(  
   out IDebugProcess2 ppProcess  
);  
```  
  
#### Parámetros  
 `ppProcess`  
 \[out\]  devuelve la interfaz de [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) que representa el proceso.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 A menos que un motor de depuración \(DE\) implementa la interfaz de [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md) , la implementación de este método debe devolver siempre `E_NOTIMPL` porque un OF no puede determinar que el proceso se ejecuta en y por tanto no puede satisfacer una implementación de este método.  
  
 Implementar la interfaz de `IDebugEngineLaunch2` significa que el OF debe saber cómo crear un proceso; por consiguiente, la implementación de la interfaz de [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) puede saber qué proceso se ejecuta en.  
  
## Vea también  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)