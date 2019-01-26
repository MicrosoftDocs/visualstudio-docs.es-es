---
title: Procesos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 85cfadc626ac28061ec91da2ea1c0d9c063994bb
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54948207"
---
# <a name="processes"></a>Procesos
En la arquitectura de depurador, un *proceso*:  
  
- Es un contenedor para un conjunto de programas. Es prácticamente análoga a un proceso de Windows, que es un contenedor para un conjunto de subprocesos.  
  
- Puede identificarse por nombre, identificador o identificador físico.  
  
- Puede enumerar todos los programas en ejecución (y sus subprocesos).  
  
- Puede describir propio, el puerto en que se está ejecutando y el equipo que lo contiene.  
  
- Puede crear uno o más programas, finalizar alguno de los programas que crea o hacer que un programa detener.  
  
- Se representa mediante un [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) interfaz, que se crea cuando se inicia el proceso. Se inicia un proceso en la sesión Administrador de depuración (SDM) o [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
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