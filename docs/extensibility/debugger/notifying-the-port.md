---
title: Notificación al puerto de la Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738316"
---
# <a name="notify-the-port"></a>Notificar al puerto
Después de iniciar un programa, el puerto debe ser notificado, de la siguiente manera:

1. Cuando un puerto recibe un nuevo nodo de programa, envía un evento de creación de programa a la sesión de depuración. El evento lleva conlleva una interfaz que representa el programa.

2. La sesión de depuración consulta el programa para el identificador de un motor de depuración (DE) que se puede asociar a.

3. La sesión de depuración comprueba si el DE está en la lista de DE permitidos para ese programa. La sesión de depuración obtiene esta lista de la configuración del programa activo de la solución, que el paquete de depuración le pasó originalmente.

    El DE debe estar en la lista permitida, o de lo contrario el DE no se adjuntará al programa.

   Mediante programación, cuando un puerto recibe por primera vez un nuevo nodo de programa, crea una interfaz [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) para representar el programa.

> [!NOTE]
> Esto no debe confundirse con la `IDebugProgram2` interfaz creada más adelante por el motor de depuración (DE).

 El puerto envía un evento de creación de programa [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) al administrador `IConnectionPoint` de depuración de sesión (SDM) mediante una interfaz COM.

> [!NOTE]
> Esto no debe confundirse con la `IDebugProgramCreateEvent2` interfaz, que es enviada más adelante por el DE.

 Junto con la propia interfaz de eventos, el puerto envía las interfaces [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md), [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)e [IDebugProgram2,](../../extensibility/debugger/reference/idebugprogram2.md) que representan el puerto, el proceso y el programa, respectivamente. El SDM llama [a IDebugProgram2::GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) para obtener el GUID de la DE que puede depurar el programa. El GUID se obtuvo originalmente de la [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) interfaz.

 El SDM marca para ver si el DE está en la lista de DE permitidos. El SDM obtiene esta lista de la configuración del programa activo de la solución, que el paquete de depuración le pasó originalmente. El DE debe estar en la lista permitida, o de lo contrario no se adjuntará al programa.

 Una vez que se conoce la identidad del DE, el SDM está listo para adjuntarlo al programa.

## <a name="see-also"></a>Vea también
- [Lanzamiento de un programa](../../extensibility/debugger/launching-a-program.md)
- [Adjuntar después de un lanzamiento](../../extensibility/debugger/attaching-after-a-launch.md)
- [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)
