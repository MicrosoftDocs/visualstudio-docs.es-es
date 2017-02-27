---
title: "DEBUG_REASON | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DEBUG_REASON"
helpviewer_keywords: 
  - "Enumeración DEBUG_REASON"
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# DEBUG_REASON
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Especifica qué el proceso se inicia para depurar.  
  
## Sintaxis  
  
```cpp#  
enum enum_DEBUG_REASON {  
   DEBUG_REASON_ERROR         = 0,  
   DEBUG_REASON_USER_LAUNCHED = 1,  
   DEBUG_REASON_USER_ATTACHED = 2,  
   DEBUG_REASON_AUTO_ATTACHED = 3,  
   DEBUG_REASON_CAUSALITY     = 4  
};  
typedef DWORD DEBUG_REASON;  
```  
  
```c#  
public enum enum_DEBUG_REASON {  
   DEBUG_REASON_ERROR         = 0,  
   DEBUG_REASON_USER_LAUNCHED = 1,  
   DEBUG_REASON_USER_ATTACHED = 2,  
   DEBUG_REASON_AUTO_ATTACHED = 3,  
   DEBUG_REASON_CAUSALITY     = 4  
};  
```  
  
#### Parámetros  
 DEBUG\_REASON\_ERROR  
 Un error no específico producido \(se utiliza como condición predeterminada cuando ninguna de las otras razones caben\).  
  
 DEBUG\_REASON\_USER\_LAUNCHED  
 El proceso se inicia en la solicitud de usuario.  
  
 DEBUG\_REASON\_USER\_ATTACHED  
 El proceso de ya\-funcionamiento se adjuntó por el usuario.  
  
 DEBUG\_REASON\_AUTO\_ATTACHED  
 El proceso automáticamente estaba adjunto a cuando se inicia.  
  
 DEBUG\_REASON\_CAUSALITY  
 El proceso se inicia debido a un evento \(JIT\) de depuración Just\-In\-Time.  
  
## Comentarios  
 Volver del método de [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md) .  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)