---
title: Notificación del puerto | Microsoft Docs
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
- ports, notification
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4faaea47196e6d247aa62c5a9d067970ddeaaec4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49937076"
---
# <a name="notifying-the-port"></a>Notificación del puerto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Después de iniciar un programa, el puerto debe recibir una notificación, como sigue:  
  
1. Cuando un puerto recibe un nuevo nodo de programa, envía el evento de creación de un programa a la sesión de depuración. El evento conlleva una interfaz que representa el programa.  
  
2. El programa para el identificador de un motor de depuración (DE) que puede adjuntar a consulta a la sesión de depuración.  
  
3. La sesión de depuración comprueba si es la DE en la lista de permitidos DEs para ese programa. La sesión de depuración, obtiene esta lista de configuración del programa activo de la solución, pasado originalmente por el paquete de depuración.  
  
    Debe ser la DE la lista de permitidos, o bien la DE no se adjuntará al programa.  
  
   Mediante programación, cuando un puerto recibe un nuevo nodo de programa por primera vez, crea un [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) interfaz para representar el programa.  
  
> [!NOTE]
>  No debe confundirse con el `IDebugProgram2` interfaz posterior creada por el motor de depuración (DE).  
  
 El puerto envía una [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) evento de creación de programa al administrador de depuración de sesión (SDM) por medio de COM `IConnectionPoint` interfaz.  
  
> [!NOTE]
>  No debe confundirse con el `IDebugProgramCreateEvent2` interfaz, que la DE enviar más tarde.  
  
 Junto con la propia interfaz de eventos, el puerto envía el [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md), [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md), y [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) interfaces, que representan el puerto, procesan, y programa, respectivamente. Las llamadas SDM [IDebugProgram2::GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) para obtener el GUID de la DE que puede depurar el programa. El GUID se ha obtenido originalmente de la [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) interfaz.  
  
 Comprueba el SDM para ver si la DE la lista de permitidos DEs. El SDM obtiene esta lista de configuración del programa activo de la solución, pasado originalmente por el paquete de depuración. Debe ser la DE la lista de permitidos, o bien no se adjuntará al programa.  
  
 Una vez que se conoce la identidad de la DE, el SDM está listo para adjuntarlo al programa.  
  
## <a name="see-also"></a>Vea también  
 [Iniciar un programa](../../extensibility/debugger/launching-a-program.md)   
 [Asociar después de un lanzamiento](../../extensibility/debugger/attaching-after-a-launch.md)   
 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)

