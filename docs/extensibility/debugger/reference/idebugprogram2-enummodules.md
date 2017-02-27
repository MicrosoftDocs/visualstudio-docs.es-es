---
title: "IDebugProgram2::EnumModules | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::EnumModules"
helpviewer_keywords: 
  - "IDebugProgram2::EnumModules"
ms.assetid: 876ac9da-3b7c-4156-b79a-8f340e9fcea6
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProgram2::EnumModules
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

recupera una lista de los módulos que este programa ha cargado y se está ejecutando.  
  
## Sintaxis  
  
```cpp#  
HRESULT EnumModules(   
   IEnumDebugModules2** ppEnum  
);  
```  
  
```c#  
int EnumModules(   
   out IEnumDebugModules2 ppEnum  
);  
```  
  
#### Parámetros  
 `ppEnum`  
 \[out\]  Devuelve un objeto de [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) que contiene una lista de los módulos.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Un módulo es un archivo DLL o un ensamblado y se muestra normalmente en la ventana de depuración de **Módulos** .  
  
## Vea también  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)