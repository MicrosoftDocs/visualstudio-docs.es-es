---
title: "IDebugDefaultPort2::GetServer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDefaultPort2::GetServer"
helpviewer_keywords: 
  - "IDebugDefaultPort2::GetServer"
ms.assetid: cacb4b74-0f39-471c-af38-54b73f5b2868
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDefaultPort2::GetServer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Este método obtiene una interfaz al servidor que este puerto está activado.  
  
## Sintaxis  
  
```cpp  
HRESULT GetServer(  
   IDebugCoreServer3** ppServer  
);  
```  
  
```c#  
int GetServer(  
   out IDebugCoreServer3 ppServer  
);  
```  
  
#### Parámetros  
 `ppServer`  
 \[out\]  devuelve un objeto que implementa la interfaz de [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) .  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) se implementa mediante Visual Studio y representa el servidor que el puerto se encuentra en.  
  
## Vea también  
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)