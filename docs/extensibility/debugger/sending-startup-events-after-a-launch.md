---
title: "Enviar eventos de inicio despu&#233;s de un lanzamiento | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "depurar [SDK de depuración], eventos de inicio"
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Enviar eventos de inicio despu&#233;s de un lanzamiento
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

El motor de depuración \(DE\) se asocia una vez al programa, envía una serie de eventos startup de nuevo a la sesión de depuración.  
  
 Eventos startup enviados posterior a la sesión de depuración lo siguiente:  
  
-   Un evento de creación del motor.  
  
-   Un evento de creación de programa.  
  
-   Eventos de creación y la carga de módulos de subproceso.  
  
-   Una carga completa el evento, incluido cuando se carga el código y listo para ejecutarse, pero antes de que se ejecuta todo el código  
  
    > [!NOTE]
    >  Cuando se continúa este evento, se inicializan las variables globales y ejecución de las rutinas de arranque.  
  
-   Otro posible eventos de creación y la carga de módulos de subproceso.  
  
-   Un evento de punto de entrada, que indica que el programa ha alcanzado el punto de entrada principal, como **Principal** o `WinMain`.  Este evento no se envía normalmente si el OF asocia un programa que se está ejecutando.  
  
 Mediante programación, el OF envía primero el administrador de depuración de sesión \(SDM\) una interfaz de [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) , que representa un evento de creación del motor, seguida de [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md), que representa un evento de creación de programa.  
  
 Esto va seguida normalmente por uno o más eventos de los eventos de la creación de subprocesos de [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) y la carga de módulos de [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) .  
  
 Cuando se carga el código y listo para ejecutarse, pero antes de que se ejecuta el código, el OF envía el SDM un evento completed carga de [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) .  Por último, si el programa no se está ejecutando, el OF envía un evento de punto de entrada de [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) , indica que el programa ha alcanzado el punto de entrada principal y está listo para depurar.  
  
## Vea también  
 [Control de ejecución](../../extensibility/debugger/control-of-execution.md)   
 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)