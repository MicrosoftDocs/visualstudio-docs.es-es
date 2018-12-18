---
title: Envío de eventos de inicio después de un lanzamiento | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 64a2423e3e6900d992ba1a2fafe13f72ab329520
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49927078"
---
# <a name="send-startup-events-after-a-launch"></a>Enviar eventos de inicio después de un lanzamiento
Una vez que el motor de depuración (DE) está asociado al programa, envía una serie de eventos de inicio a la sesión de depuración.  
  
 Eventos de inicio que se envían a la sesión de depuración incluyen:  
  
- Evento de creación de un motor.  
  
- Evento de creación de un programa.  
  
- Subproceso de creación y eventos del módulo de carga.  
  
- Un evento completo de carga, enviado cuando el código está cargado y listo para ejecutarse, pero antes de ejecutar cualquier código. 
  
  > [!NOTE]
  >  Cuando este evento continúa, se inicializan las variables globales y ejecutan rutinas de inicio.  
  
- Posibles otros eventos del módulo de carga y de creación de subprocesos.  
  
- Un evento de punto de entrada, lo cual indica que el programa ha alcanzado su punto de entrada principal, como **Main** o `WinMain`. Este evento normalmente no se envía si la DE que se asocia a un programa que ya se está ejecutando.  
  
  Mediante programación, la DE envía primero el Administrador de depuración de la sesión (SDM) un [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) interfaz, que representa un evento de creación del motor, seguido por un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) , que representa el evento de creación de un programa.  
  
  Estos eventos se siguen normalmente por uno o varios [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) eventos de creación de subprocesos y [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) eventos del módulo de carga.  
  
  Cuando el código está cargado y listo para ejecutarse, pero antes de ejecutar cualquier código, la DE envía el SDM un [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) eventos de carga completa. Por último, si ya no se está ejecutando el programa, la DE envía una [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) evento de punto de entrada, de señalización que el programa ha alcanzado su punto de entrada principal y está listo para la depuración.  
  
## <a name="see-also"></a>Vea también  
 [Control de ejecución](../../extensibility/debugger/control-of-execution.md)   
 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)