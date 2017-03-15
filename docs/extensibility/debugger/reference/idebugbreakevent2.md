---
title: "IDebugBreakEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBreakEvent2"
helpviewer_keywords: 
  - "Interfaz IDebugBreakEvent2"
ms.assetid: 57dfdbc2-4e68-4dbf-9579-006cd6fb1c62
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugBreakEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz indica al administrador de depuración de la sesión \(SDM\) que una interrupción asincrónica se haya completado correctamente.  
  
## Sintaxis  
  
```  
IDebugBreakEvent2 : IUnknown  
```  
  
## Notas para los implementadores  
 El OF implementa esta interfaz para admitir saltos de usuario en un programa.  la interfaz de [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) se debe implementar en el mismo objeto que esta interfaz \(el SDM utiliza [QueryInterface](/visual-cpp/atl/queryinterface) para tener acceso a la interfaz de `IDebugEvent2` \).  
  
## Notas para los llamadores  
 El SDM llama [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) cuando el usuario ha solicitado el programa que se depura para poner en pausa.  Cuando se ha pausado el programa correctamente, el OF envía el evento de `IDebugBreakEvent2` .  Este evento se envía mediante la función de devolución de llamada de [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) proporcionada por el SDM cuando adjuntó el programa que se depura.  
  
## Comentarios  
 Por ejemplo, un usuario puede elegir el comando de **Interrumpir todos** en el menú de **Depurar** de interrumpir un programa que se ejecuta un bucle infinito.  El SDM indica al programa que deje llamando a [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md).  El OF envía `IDebugBreakEvent2` cuando el programa finalmente se detiene.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)