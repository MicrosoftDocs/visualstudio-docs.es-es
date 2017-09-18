---
title: "IDebugProcessEx2::Detach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcessEx2::Detach"
helpviewer_keywords: 
  - "IDebugProcessEx2::Detach (método)"
ms.assetid: 66d54c2c-9302-47c8-9975-f30ed988ab29
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# IDebugProcessEx2::Detach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Este método informa al proceso que una sesión está depurando no más el proceso.  
  
## Sintaxis  
  
```cpp#  
HRESULT Detach(   
   IDebugSession2* pSession  
);  
```  
  
```c#  
int Detach(  
   IDebugSession2 pSession  
);  
```  
  
#### Parámetros  
 `pSession`  
 \[in\]  Un valor de que identifica de forma única a la sesión para desasociar este proceso.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 La interfaz última en `pSession` debe tratarlo solo como cookie, un valor que identifica de forma única el administrador de depuración de la sesión que adjuntó originalmente para este proceso; ninguno de los métodos en la interfaz proporcionada funcionan.  
  
## Vea también  
 [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)