---
title: Notificar el puerto | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ports, notification
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 154a5891d9a11dd77c92f3f297a2e905d40f0327
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="notifying-the-port"></a>Notificar el puerto
Después de iniciar un programa, el puerto debe recibir una notificación, como se indica a continuación:  
  
1.  Cuando un puerto recibe un nuevo nodo de programa, envía un evento de creación de programa a la sesión de depuración. El evento conlleva una interfaz que representa el programa.  
  
2.  La sesión de depuración consulta el programa para el identificador de un motor de depuración (Alemania) que puede adjuntar a.  
  
3.  La sesión de depuración comprueba si la DE se encuentra en la lista de permitidos DEs para ese programa. La sesión de depuración obtiene esta lista de configuración del programa activo de la solución, originalmente ha pasado el paquete de depuración.  
  
     Debe ser la DE la lista de permitidos o, de lo contrario, no se adjuntará el Alemania al programa.  
  
 Mediante programación, cuando un puerto recibe un nuevo nodo de programa por primera vez, crea un [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) interfaz para representar el programa.  
  
> [!NOTE]
>  No debe confundirse con el `IDebugProgram2` interfaz posterior creada por el motor de depuración (Alemania).  
  
 El puerto envía una [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) eventos de creación de programa hacia el Administrador de sesión de depuración (SDM) por medio de un COM `IConnectionPoint` interfaz.  
  
> [!NOTE]
>  No debe confundirse con el `IDebugProgramCreateEvent2` interfaz, que la DE enviar más tarde.  
  
 Junto con la propia interfaz de eventos, el puerto envía el [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md), [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md), y [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) , las interfaces que representan el puerto, procesan, y programa, respectivamente. Las llamadas SDM [IDebugProgram2::GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) para obtener el GUID de la DE que puede depurar el programa. El GUID originalmente se obtuvo de la [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) interfaz.  
  
 El SDM comprueba si es la DE la lista de permitidos DEs. El SDM obtiene esta lista de configuración del programa activo de la solución, originalmente ha pasado el paquete de depuración. Debe ser la DE la lista de permitidos o, de lo contrario, no se adjuntará al programa.  
  
 Una vez que se conoce la identidad de la DE, el SDM está listo para adjuntar al programa.  
  
## <a name="see-also"></a>Vea también  
 [Ejecutar un programa](../../extensibility/debugger/launching-a-program.md)   
 [Adjuntar después de un lanzamiento](../../extensibility/debugger/attaching-after-a-launch.md)   
 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)