---
title: "IDebugThreadNameChangedEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugThreadNameChangedEvent2"
helpviewer_keywords: 
  - "IDebugThreadNameChangedEvent2"
ms.assetid: 34c1652e-f019-48ba-8b26-ace20f8a158c
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugThreadNameChangedEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz es enviada por el motor de depuración al \(DE\) administrador de depuración de sesión \(SDM\) a los cambios de nombre de un subproceso en el programa que se depura.  
  
## Sintaxis  
  
```  
IDebugThreadNameChangedEvent2 : IUnknown  
```  
  
## Notas para los implementadores  
 El OF implementa esta interfaz para indicar que el nombre de un subproceso ha cambiado.  la interfaz de [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) se debe implementar en el mismo objeto que esta interfaz.  El SDM utiliza [QueryInterface](/visual-cpp/atl/queryinterface) para tener acceso a la interfaz de `IDebugEvent2` .  
  
## Notas para los llamadores  
 El OF crea y envía este objeto event para indicar que el nombre de un subproceso ha cambiado.  El evento se envía mediante la función de devolución de llamada de [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) proporcionada por el SDM cuando se asocia al programa que se depura.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)