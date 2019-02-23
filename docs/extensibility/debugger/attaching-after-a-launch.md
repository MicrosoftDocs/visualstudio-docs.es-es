---
title: Asociar después de un lanzamiento | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 54284b9e1e55e4e3a3ba8b8237b9420cbf195089
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56704051"
---
# <a name="attach-after-a-launch"></a>Adjuntar después de un lanzamiento
Una vez que inicia un programa, la sesión de depuración está lista para asociar el motor de depuración (DE) a dicho programa.

## <a name="design-decisions"></a>Decisiones de diseño
 Puesto que la comunicación es más fácil dentro de un espacio de direcciones compartido, debe elegir entre dos enfoques de diseño: establecer la comunicación entre la sesión de depuración y la DE. O bien, establezca la comunicación entre el programa y la DE. Elija entre lo siguiente:

-   Si tiene más sentido para configurar la comunicación entre la sesión de depuración y la DE, la sesión de depuración participa en la DE la creación y solicita la DE asociar al programa. Este diseño deja la sesión de depuración y DE juntos en un espacio de direcciones y el entorno de tiempo de ejecución y el programa juntos en otro.

-   Si tiene más sentido para configurar la comunicación entre el programa y la DE, el entorno de tiempo de ejecución crea conjuntamente la DE. Este diseño deja el SDM en un espacio de direcciones y el DE, el entorno de tiempo de ejecución y el programa juntos en otro. Este diseño es típico de una DE que se implementa con un intérprete para ejecutarse con secuencias de comandos de idiomas.

    > [!NOTE]
    >  Cómo la DE se une al programa es depende de la implementación. Comunicación entre el programa y la DE es también depende de la implementación.

## <a name="implementation"></a>Implementación
 Mediante programación, cuando el Administrador de depuración de la sesión (SDM) recibe por primera vez el [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) objeto que representa el programa se inicie, llama a la [adjuntar](../../extensibility/debugger/reference/idebugprogram2-attach.md) método y pásele un [ IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) objeto, que es una versión posterior se usa para pasar los eventos de depuración hasta el SDM. El `IDebugProgram2::Attach` método, a continuación, llama a la [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) método. Para obtener más información sobre cómo el SDM recibe el `IDebugProgram2` interfaz, vea [notificación del puerto](../../extensibility/debugger/notifying-the-port.md).

 Si debe ejecutarse en el mismo espacio de direcciones que el programa de la DE depuración: dado que la DE suele ser parte de un intérprete que se está ejecutando un script, el `IDebugProgramNodeAttach2::OnAttach` devuelve del método `S_FALSE`. El `S_FALSE` retorno indica que finalizado el proceso de conexión.

 Si, sin embargo, la DE se ejecuta en el espacio de direcciones del SDM: el `IDebugProgramNodeAttach2::OnAttach` devuelve del método `S_OK`, o el [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) interfaz no está implementada en absoluto en el [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) objeto asociado con el programa se está depurando. En este caso, el [adjuntar](../../extensibility/debugger/reference/idebugengine2-attach.md) finalmente se llama el método para completar la operación de adjuntar.

 En el último caso, se debe llamar a la [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) método en el `IDebugProgram2` objeto que se pasó a la `IDebugEngine2::Attach` método, la tienda la `GUID` en el sistema local de objetos y devolver este `GUID` cuando el `IDebugProgram2::GetProgramId` se llama al método en este objeto. El `GUID` se usa para identificar de forma única el programa a través de los distintos componentes de depuración.

 En el caso de los `IDebugProgramNodeAttach2::OnAttach` método que devuelve `S_FALSE`, el `GUID` que se usará para el programa se pasa a ese método y es el `IDebugProgramNodeAttach2::OnAttach` método que establece el `GUID` en el objeto de sistema local.

 La DE está ahora conectada al programa y está listo para enviar los eventos de inicio.

## <a name="see-also"></a>Vea también
- [Asociación directamente a un programa](../../extensibility/debugger/attaching-directly-to-a-program.md)
- [Notificación del puerto](../../extensibility/debugger/notifying-the-port.md)
- [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)
- [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [Asociar](../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Asociar](../../extensibility/debugger/reference/idebugengine2-attach.md)