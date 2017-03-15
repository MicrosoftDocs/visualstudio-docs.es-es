---
title: "IDebugExceptionEvent2::CanPassToDebuggee | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExceptionEvent2::CanPassToDebuggee"
helpviewer_keywords: 
  - "IDebugExceptionEvent2::CanPassToDebuggee"
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugExceptionEvent2::CanPassToDebuggee
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Determina si el motor de depuración \(DE\) admite la opción de pasar esta excepción al programa que se está depurando cuando la ejecución se reanuda.  
  
## Sintaxis  
  
```cpp#  
HRESULT CanPassToDebuggee(  
   void  
);  
```  
  
```c#  
int CanPassToDebuggee();  
```  
  
## Valor devuelto  
 Devuelve `S_OK` \(la excepción se puede pasar al programa\) o `S_FALSE` \(la excepción no se puede pasar en\).  
  
## Comentarios  
 El OF debe tener una acción predeterminada para pasar al código que está siendo depurado.  El IDE puede recibir el evento de [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) y llamar al método de [Continuar](../../../extensibility/debugger/reference/idebugprocess3-continue.md) sin llamar al método de `CanPassToDebuggee` .  Por consiguiente, el OF debe tener un caso predeterminado para pasar la excepción en o no.  
  
## Vea también  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [Continuar](../../../extensibility/debugger/reference/idebugprocess3-continue.md)