---
title: "Envío de eventos de inicio después de un inicio | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 65e05d7da2acf5bd3eaf8dab1e3781d3d5b244a0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="sending-startup-events-after-a-launch"></a>Envío de eventos de inicio después de un lanzamiento
Una vez que el motor de depuración (Alemania) se asocian al programa, envía una serie de eventos de inicio a la sesión de depuración.  
  
 Eventos de inicio que se envían a la sesión de depuración incluyen lo siguiente:  
  
-   Un evento de creación de motor.  
  
-   Evento de creación de un programa.  
  
-   Subprocesos de creación y eventos del módulo de carga.  
  
-   Un evento de carga completada, enviado cuando el código está cargado y listo para ejecutarse, pero antes de ejecutar cualquier código  
  
    > [!NOTE]
    >  Cuando se sigue este evento, se inicializan las variables globales y ejecutan rutinas de inicio.  
  
-   Posible otro subprocesos creación y eventos del módulo de carga.  
  
-   Un evento de punto de entrada, lo cual indica que el programa ha alcanzado su punto de entrada principal, como **Main** o `WinMain`. Este evento no se envía normalmente si el Alemania se asocia a un programa que ya se está ejecutando.  
  
 Mediante programación, la DE envía primero el Administrador de sesión de depuración (SDM) un [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) interfaz, que representa un evento de creación de motor, seguido por un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) , que representa un evento de creación de programa.  
  
 Esto le sigue normalmente uno o varios [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) eventos de creación de subprocesos y [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) eventos del módulo de carga.  
  
 Cuando el código está cargado y listo para ejecutarse, pero antes de ejecuta cualquier código, la DE envía el SDM un [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) eventos de carga completa. Por último, si el programa no se está ejecutando, la DE envía una [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) evento de punto de entrada, que el programa ha llegado a su punto de entrada principal y está listo para la depuración de señalización.  
  
## <a name="see-also"></a>Vea también  
 [Control de ejecución](../../extensibility/debugger/control-of-execution.md)   
 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)