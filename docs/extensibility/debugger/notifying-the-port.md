---
title: Notificar el puerto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports, notification
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff94c20969e77bcc70af2f5a16137e09366a0d7d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738316"
---
# <a name="notify-the-port"></a>Notificar el puerto
Después de iniciar un programa, el puerto debe recibir una notificación, como se indica a continuación:

1. Cuando un puerto recibe un nuevo nodo de programa, vuelve a enviar un evento de creación de programa a la sesión de depuración. El evento lleva una interfaz que representa el programa.

2. La sesión de depuración consulta el programa para el identificador de un motor de depuración (DE) que se puede adjuntar a.

3. La sesión de depuración comprueba si el DE está en la lista de DEs permitidos para ese programa. La sesión de depuración obtiene esta lista de la configuración de programa activa de la solución, que se le pasó originalmente mediante el paquete de depuración.

    El DE debe estar en la lista de permitidos o, DE lo contrario, no se adjuntará al programa.

   Mediante programación, cuando un puerto recibe primero un nuevo nodo de programa, crea una interfaz [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) para representar el programa.

> [!NOTE]
> Esto no se debe confundir con la `IDebugProgram2` interfaz creada posteriormente por el motor de depuración (de).

 El puerto envía un evento de creación del programa [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) al administrador de depuración de la sesión (SDM) mediante una `IConnectionPoint` interfaz com.

> [!NOTE]
> Esto no se debe confundir con la `IDebugProgramCreateEvent2` interfaz, que se envía posteriormente por el de.

 Junto con la propia interfaz de eventos, el puerto envía las interfaces [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md), [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)y [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) , que representan el puerto, el proceso y el programa, respectivamente. El SDM llama a [IDebugProgram2:: GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) para obtener el GUID del de que puede depurar el programa. El GUID se obtuvo originalmente de la interfaz [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) .

 El SDM realiza comprobaciones para ver si el DE está en la lista de DEs permitido. El SDM obtiene esta lista de la configuración de programa activa de la solución, que se le pasó originalmente mediante el paquete de depuración. El DE debe estar en la lista de permitidos o, de lo contrario, no se adjuntará al programa.

 Una vez que se conoce la identidad de de, el SDM está listo para adjuntarlo al programa.

## <a name="see-also"></a>Vea también
- [Iniciar un programa](../../extensibility/debugger/launching-a-program.md)
- [Adjuntar después de un inicio](../../extensibility/debugger/attaching-after-a-launch.md)
- [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)
