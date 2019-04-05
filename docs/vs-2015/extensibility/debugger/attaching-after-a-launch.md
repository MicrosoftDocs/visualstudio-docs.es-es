---
title: Asociar después de un lanzamiento | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b1f39297c4e87b7d4801b786ca2132acaf366fd3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58999257"
---
# <a name="attaching-after-a-launch"></a>Asociación tras el inicio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Después de que se ha iniciado un programa, la sesión de depuración está lista para asociar el motor de depuración (DE) a dicho programa.  
  
## <a name="design-decisions"></a>Decisiones de diseño  
 Dado que la comunicación es más fácil dentro de un espacio de direcciones compartido, debe decidir si tiene más sentido para facilitar la comunicación entre la sesión de depuración y la DE o entre la DE y el programa. Elija entre lo siguiente:  
  
-   Si tiene más sentido para facilitar la comunicación entre la sesión de depuración y la DE, la sesión de depuración participa en la DE la creación y solicita la DE asociar al programa. Esto deja la sesión de depuración y DE juntos en un espacio de direcciones y el entorno de tiempo de ejecución y el programa juntos en otro.  
  
-   Si tiene más sentido para facilitar la comunicación entre la DE y el programa, el entorno de tiempo de ejecución crea conjuntamente la DE. Esto deja el SDM en un espacio de direcciones y el DE, el entorno de tiempo de ejecución y el programa juntos en otro. Esto es típico de una DE que se implementa con un intérprete para ejecutarse con secuencias de comandos de idiomas.  
  
    > [!NOTE]
    >  Cómo la DE se une al programa es depende de la implementación. Comunicación entre el programa y la DE es también depende de la implementación.  
  
## <a name="implementation"></a>Implementación  
 Mediante programación, cuando el Administrador de depuración de la sesión (SDM) recibe por primera vez el [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) objeto que representa el programa se inicie, llama a la [adjuntar](../../extensibility/debugger/reference/idebugprogram2-attach.md) método y pásele un [ IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) objeto, que es una versión posterior se usa para pasar los eventos de depuración hasta el SDM. El `IDebugProgram2::Attach` método, a continuación, llama a la [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) método. Para obtener más información sobre cómo el SDM recibe el `IDebugProgram2` interfaz, vea [notificación del puerto](../../extensibility/debugger/notifying-the-port.md).  
  
 Si debe ejecutarse en el mismo espacio de direcciones que el programa que se está depurando, normalmente porque forma parte de un intérprete en ejecución de una secuencia de comandos, la DE los DE la `IDebugProgramNodeAttach2::OnAttach` devuelve del método `S_FALSE`, que indica que ha completado el proceso de conexión.  
  
 Si, por otro lado, la DE se ejecuta en el espacio de direcciones del SDM, la `IDebugProgramNodeAttach2::OnAttach` devuelve del método `S_OK` o [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) interfaz no está implementada en absoluto en el [IDebugProgramNode2 ](../../extensibility/debugger/reference/idebugprogramnode2.md) objeto asociado con el programa que se está depurando. En este caso, el [adjuntar](../../extensibility/debugger/reference/idebugengine2-attach.md) finalmente se llama el método para completar la operación de adjuntar.  
  
 En el último caso, se debe llamar a la [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) método en el `IDebugProgram2` objeto que se pasó a la `IDebugEngine2::Attach` método, la tienda la `GUID` en el sistema local de objetos y devolver este `GUID` cuando el `IDebugProgram2::GetProgramId` se llama al método en este objeto. El `GUID` se usa para identificar de forma única el programa a través de los distintos componentes de depuración.  
  
 Tenga en cuenta que en el caso de los `IDebugProgramNodeAttach2::OnAttach` método que devuelve `S_FALSE`, el `GUID` que se usará para el programa se pasa a ese método y es el `IDebugProgramNodeAttach2::OnAttach` método que establece el `GUID` en el objeto de sistema local.  
  
 La DE está ahora conectada al programa y está listo para enviar los eventos de inicio.  
  
## <a name="see-also"></a>Vea también  
 [Asociación directamente a un programa](../../extensibility/debugger/attaching-directly-to-a-program.md)   
 [Notificación del puerto](../../extensibility/debugger/notifying-the-port.md)   
 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)   
 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [Adjuntar](../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Asociar](../../extensibility/debugger/reference/idebugengine2-attach.md)
