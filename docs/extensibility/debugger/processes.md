---
title: Procesos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 75230740e84bb6660629b38e84df56fa8e5c1856
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="processes"></a>Procesos
En cuanto a la arquitectura del depurador, una **proceso**:  
  
-   Es un contenedor para un conjunto de programas. Es prácticamente análoga a un proceso de Windows, que es un contenedor para un conjunto de subprocesos.  
  
-   Puede identificarse por nombre, identificador o identificador físico.  
  
-   Puede enumerar todos los programas en ejecución (y sus subprocesos).  
  
-   Puede describir sí solo, el puerto en que se está ejecutando y el equipo que lo contiene.  
  
-   Puede crear uno o más programas, terminar cualquiera de los programas crea o que un programa se detenga.  
  
-   Se representa mediante un [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) interfaz, que se crea cuando se inicia el proceso. Se inicia un proceso por cualquier sesión el Administrador de depuración (SDM) o [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
 El paquete de depuración puede asociar un motor de depuración (Alemania) a un proceso mediante una llamada a [adjuntar](../../extensibility/debugger/reference/idebugprocess2-attach.md). Esto significa que la DE se asocia a todos los programas posibles que se ejecuta en el proceso que puede controlar. Por ejemplo, si common language runtime Alemania se asocia a un proceso, se adjunta solo a los programas que utilizan código administrado.  
  
## <a name="see-also"></a>Vea también  
 [Programas](../../extensibility/debugger/programs.md)   
 [Subprocesos](../../extensibility/debugger/threads.md)   
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)   
 [Depurar paquete](../../extensibility/debugger/debug-package.md)   
 [Motor de depuración](../../extensibility/debugger/debug-engine.md)   
 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Asociar](../../extensibility/debugger/reference/idebugprocess2-attach.md)