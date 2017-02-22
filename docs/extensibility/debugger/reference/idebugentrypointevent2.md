---
title: "IDebugEntryPointEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEntryPointEvent2"
helpviewer_keywords: 
  - "Interfaz IDebugEntryPointEvent2"
ms.assetid: a15d1cc3-97b7-438c-8d24-c23149708f42
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEntryPointEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

El motor de depuración \(DE\) envía esta interfaz al administrador \(SDM\) de depuración de la sesión cuando el programa es de ejecutar la primera instrucción del código de usuario.  
  
## Sintaxis  
  
```  
IDebugEntryPointEvent2 : IUnknown  
```  
  
## Notas para los implementadores  
 El OF implementa esta interfaz como parte de las operaciones normales.  la interfaz de [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) se debe implementar en el mismo objeto que esta interfaz.  El SDM utiliza [QueryInterface](/visual-cpp/atl/queryinterface) para tener acceso a la interfaz de `IDebugEvent2` .  
  
## Notas para los llamadores  
 El OF crea y envía este objeto event cuando el programa que se depura ha cargado y está listo para ejecutar la primera instrucción del código de usuario.  El evento se envía mediante la función de devolución de llamada de [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) proporcionada por el SDM cuando adjuntó el programa que se depura.  
  
## Comentarios  
 Se envía[IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) cuando el programa es de ejecutar la primera instrucción.  Por ejemplo, se envía `IDebugEntryPoint2` cuando el programa va a ejecutar la función de `main` de usuario.  
  
 Cuando el OF envía `IDebugEntryPointEvent2`, la posición actual de código debe estar en la primera instrucción del código de usuario, como `main`.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)