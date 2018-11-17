---
title: Procesos | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6428b6cb3a3bedac6b1deae35fd2cd7f501d70f8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51809888"
---
# <a name="processes"></a>Procesos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En cuanto a la arquitectura de depurador, un **proceso**:  
  
- Es un contenedor para un conjunto de programas. Es prácticamente análoga a un proceso de Windows, que es un contenedor para un conjunto de subprocesos.  
  
- Puede identificarse por nombre, identificador o identificador físico.  
  
- Puede enumerar todos los programas en ejecución (y sus subprocesos).  
  
- Puede describir propio, el puerto en que se está ejecutando y el equipo que lo contiene.  
  
- Puede crear uno o más programas, finalizar alguno de los programas que crea o hacer que un programa detener.  
  
- Se representa mediante un [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) interfaz, que se crea cuando se inicia el proceso. Se inicia un proceso en la sesión Administrador de depuración (SDM) o [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
  El paquete de depuración puede asociar un motor de depuración (DE) a un proceso mediante una llamada a [adjuntar](../../extensibility/debugger/reference/idebugprocess2-attach.md). Esto significa que la DE adjunta a todos los programas posibles que se ejecutan en el proceso que puede controlar. Por ejemplo, si common language runtime DE se asocia a un proceso, asocia únicamente a los programas que ejecutan código administrado.  
  
## <a name="see-also"></a>Vea también  
 [Programas](../../extensibility/debugger/programs.md)   
 [Subprocesos](../../extensibility/debugger/threads.md)   
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)   
 [Depurar el paquete](../../extensibility/debugger/debug-package.md)   
 [Motor de depuración](../../extensibility/debugger/debug-engine.md)   
 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Asociar](../../extensibility/debugger/reference/idebugprocess2-attach.md)

