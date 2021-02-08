---
title: Adjuntar después de un inicio | Microsoft Docs
description: Cuando se inicia un programa, la sesión de depuración está lista para adjuntar el motor de depuración al programa. Elija un enfoque de diseño para la comunicación con el motor de depuración.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 22ce6497b820e1dcd37315f9d74cb97de4cc34e0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837741"
---
# <a name="attach-after-a-launch"></a>Adjuntar después de un inicio
Una vez que se inicia un programa, la sesión de depuración está lista para adjuntar el motor DE depuración (DE) a dicho programa.

## <a name="design-decisions"></a>Decisiones de diseño
 Dado que la comunicación es más fácil dentro de un espacio de direcciones compartido, debe elegir entre dos enfoques DE diseño: establecer la comunicación entre la sesión DE depuración y la DE. O bien, establezca la comunicación entre el y el programa. Elija entre lo siguiente:

- Si tiene más sentido configurar la comunicación entre la sesión DE depuración y el DE, la sesión de depuración cocrea el DE y pide al DE que se adjunte al programa. Este diseño deja la sesión de depuración y se combina en un espacio de direcciones, y el entorno y el programa en tiempo de ejecución juntos en otro.

- Si tiene más sentido configurar la comunicación entre el y el programa, el entorno de tiempo de ejecución crea de forma conjunta el DE. Este diseño deja el SDM en un espacio de direcciones y el DE, el entorno en tiempo de ejecución y el programa juntos en otro. Este diseño es típico de un DE que se implementa con un intérprete para ejecutar lenguajes de scripts.

    > [!NOTE]
    > Cómo el DE se asocia al programa depende de la implementación. La comunicación entre el y el programa también depende de la implementación.

## <a name="implementation"></a>Implementación
 Mediante programación, cuando el administrador de depuración de sesión (SDM) recibe primero el objeto [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) que representa el programa que se va a iniciar, llama al método [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md) , pasándole un objeto [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) , que se usa posteriormente para pasar los eventos de depuración de vuelta al SDM. `IDebugProgram2::Attach`Después, el método llama al método [AutoAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) . Para obtener más información sobre cómo recibe el SDM la `IDebugProgram2` interfaz, consulte [notificar el puerto](../../extensibility/debugger/notifying-the-port.md).

 Si su DE tiene que ejecutarse en el mismo espacio de direcciones que el programa que se está depurando: como DE suele formar parte de un intérprete que ejecuta un script, el `IDebugProgramNodeAttach2::OnAttach` método devuelve `S_FALSE` . El `S_FALSE` valor devuelto indica que se completó el proceso de asociación.

 Sin embargo, si el DE se ejecuta en el espacio de direcciones del SDM: el `IDebugProgramNodeAttach2::OnAttach` método devuelve `S_OK` o la interfaz [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) no se implementa en absoluto en el objeto [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) asociado al programa que se está depurando. En este caso, se llama al método [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) para completar la operación de adjuntar.

 En el último caso, debe llamar al método [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) en el `IDebugProgram2` objeto que se pasó al `IDebugEngine2::Attach` método, almacenar el `GUID` en el objeto de programa local y devolverlo `GUID` cuando `IDebugProgram2::GetProgramId` se llama al método posteriormente en este objeto. `GUID`Se utiliza para identificar el programa de forma exclusiva en los distintos componentes de depuración.

 En el caso del `IDebugProgramNodeAttach2::OnAttach` método que devuelve `S_FALSE` , el que se `GUID` va a utilizar para el programa se pasa a ese método y es el `IDebugProgramNodeAttach2::OnAttach` método que establece `GUID` en el objeto de programa local.

 El DE ahora se adjunta al programa y está listo para enviar los eventos DE Inicio.

## <a name="see-also"></a>Vea también
- [Adjuntar directamente a un programa](../../extensibility/debugger/attaching-directly-to-a-program.md)
- [Notificación del puerto](../../extensibility/debugger/notifying-the-port.md)
- [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)
- [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [Adjuntar](../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Adjuntar](../../extensibility/debugger/reference/idebugengine2-attach.md)
