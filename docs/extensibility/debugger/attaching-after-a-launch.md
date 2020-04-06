---
title: Colocación después de un lanzamiento ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3a4ce0a7465891035b43bbb8f6f22f0c064d104c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739285"
---
# <a name="attach-after-a-launch"></a>Adjuntar después de un lanzamiento
Después de que se inicie un programa, la sesión de depuración está lista para adjuntar el motor de depuración (DE) a dicho programa.

## <a name="design-decisions"></a>Decisiones de diseño
 Dado que la comunicación es más fácil dentro de un espacio de direcciones compartido, debe elegir entre dos enfoques de diseño: establecer la comunicación entre la sesión de depuración y la DE. O bien, establezca la comunicación entre el DE y el programa. Elija entre lo siguiente:

- Si tiene más sentido configurar la comunicación entre la sesión de depuración y el DE, la sesión de depuración crea automáticamente el DE y pide que el DE se asocie al programa. Este diseño deja la sesión de depuración y DE juntas en un espacio de direcciones, y el entorno y el programa en tiempo de ejecución juntos en otro.

- Si tiene más sentido configurar la comunicación entre el DE y el programa, el entorno en tiempo de ejecución crea automáticamente el DE. Este diseño deja el SDM en un espacio de direcciones y el DE, el entorno en tiempo de ejecución y el programa juntos en otro. Este diseño es típico de un DE que se implementa con un intérprete para ejecutar lenguajes con scripts.

    > [!NOTE]
    > La forma en que el DE se asocia al programa depende de la implementación. La comunicación entre el DE y el programa también depende de la implementación.

## <a name="implementation"></a>Implementación
 Mediante programación, cuando el Administrador de depuración de sesión (SDM) recibe por primera vez el [objeto IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) que representa el programa que se va a iniciar, llama al método [Attach,](../../extensibility/debugger/reference/idebugprogram2-attach.md) pasándole un objeto [IDebugEventCallback2,](../../extensibility/debugger/reference/idebugeventcallback2.md) que se usa más adelante para pasar eventos de depuración al SDM. A `IDebugProgram2::Attach` continuación, el método llama al método [OnAttach.](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) Para obtener más información sobre cómo `IDebugProgram2` el SDM recibe la interfaz, consulte [Notificación del puerto](../../extensibility/debugger/notifying-the-port.md).

 Si la DE necesita ejecutarse en el mismo espacio de direcciones que el programa que está depurando: `IDebugProgramNodeAttach2::OnAttach` dado `S_FALSE`que la DE suele formar parte de un intérprete que ejecuta un script, el método devuelve . La `S_FALSE` devolución indica que completó el proceso de conexión.

 Sin embargo, si el DE se ejecuta en `IDebugProgramNodeAttach2::OnAttach` el `S_OK`espacio de direcciones del SDM: el método devuelve , o el [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) interfaz no se implementa en absoluto en el [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) objeto asociado con el programa que está depurando. En este caso, el [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) se llama finalmente al método para completar la operación de conexión.

 En este último caso, debe llamar al `IDebugProgram2` método [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) en el `GUID` objeto que se pasó al `GUID` `IDebugEngine2::Attach` método, almacenar el objeto de programa local y devolverlo cuando se llame posteriormente al `IDebugProgram2::GetProgramId` método en este objeto. El `GUID` se utiliza para identificar el programa de forma única a través de los diversos componentes de depuración.

 En el caso `IDebugProgramNodeAttach2::OnAttach` de `S_FALSE`que `GUID` el método devuelva , el que se `IDebugProgramNodeAttach2::OnAttach` va a `GUID` usar para el programa se pasa a ese método y es el método que establece el objeto de programa local.

 El DE ahora está asociado al programa y listo para enviar cualquier evento de inicio.

## <a name="see-also"></a>Vea también
- [Adjuntar directamente a un programa](../../extensibility/debugger/attaching-directly-to-a-program.md)
- [Notificar al puerto](../../extensibility/debugger/notifying-the-port.md)
- [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)
- [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)
