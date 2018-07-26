---
title: Procesos | Microsoft Docs
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
ms.openlocfilehash: 3c07a9cb6c16f09f2f55b543087e25d85bc300c0
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/25/2018
ms.locfileid: "39251782"
---
# <a name="processes"></a>Procesos
En la arquitectura de depurador, un *proceso*:  
  
-   Es un contenedor para un conjunto de programas. Es prácticamente análoga a un proceso de Windows, que es un contenedor para un conjunto de subprocesos.  
  
-   Puede identificarse por nombre, identificador o identificador físico.  
  
-   Puede enumerar todos los programas en ejecución (y sus subprocesos).  
  
-   Puede describir propio, el puerto en que se está ejecutando y el equipo que lo contiene.  
  
-   Puede crear uno o más programas, finalizar alguno de los programas que crea o hacer que un programa detener.  
  
-   Se representa mediante un [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) interfaz, que se crea cuando se inicia el proceso. Se inicia un proceso en la sesión Administrador de depuración (SDM) o [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
 El paquete de depuración puede asociar un motor de depuración (DE) a un proceso mediante una llamada a [adjuntar](../../extensibility/debugger/reference/idebugprocess2-attach.md), lo que significa que la DE adjunta a todos los programas posibles que se ejecutan en el proceso que puede controlar. Por ejemplo, si common language runtime DE se asocia a un proceso, asocia únicamente a los programas que ejecutan código administrado.  
  
## <a name="see-also"></a>Vea también  
 [Programas](../../extensibility/debugger/programs.md)   
 [Subprocesos](../../extensibility/debugger/threads.md)   
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)   
 [Depurar el paquete](../../extensibility/debugger/debug-package.md)   
 [Motor de depuración](../../extensibility/debugger/debug-engine.md)   
 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Asociar](../../extensibility/debugger/reference/idebugprocess2-attach.md)