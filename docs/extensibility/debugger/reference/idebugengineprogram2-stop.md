---
title: "IDebugEngineProgram2::Stop | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngineProgram2::Stop"
helpviewer_keywords: 
  - "IDebugEngineProgram2::Stop"
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugEngineProgram2::Stop
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Detiene todos los subprocesos ejecutándose en este programa.  
  
## Sintaxis  
  
```cpp#  
HRESULT Stop(   
   void   
);  
```  
  
```c#  
int Stop();  
```  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Se llama a este método cuando este programa se está depurando en un entorno de la multiprogramación.  Cuando un evento que detiene de algún otro programa se recibe, este método se llama este programa.  la implementación de este método debe ser asincrónica; es decir, no todos los subprocesos se deben requerir para detener antes de que este método devuelva.  La implementación de este método puede ser tan simple como llamando al método de [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) en este programa.  
  
 No se envía ningún evento de depuración en respuesta a este método.  
  
## Vea también  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)