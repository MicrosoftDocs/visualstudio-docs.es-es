---
title: "Adjuntar después de un inicio | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 890023b8336f130cf3b8cfcfe640da46af9cf0d1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="attaching-after-a-launch"></a>Adjuntar después de un lanzamiento
Después de que se ha iniciado un programa, la sesión de depuración está lista para asociar el motor de depuración (Alemania) a dicho programa.  
  
## <a name="design-decisions"></a>Decisiones de diseño  
 Dado que la comunicación es más fácil dentro de un espacio de direcciones compartido, debe decidir si tiene más sentido para facilitar la comunicación entre la sesión de depuración y la DE o entre el Alemania y el programa. Elija entre lo siguiente:  
  
-   Si tiene más sentido para facilitar la comunicación entre la sesión de depuración y la DE, la sesión de depuración participa en la DE la creación y solicita la DE para adjuntar al programa. Esto deja la sesión de depuración y Alemania juntos en un espacio de direcciones y el entorno en tiempo de ejecución y el programa en otro.  
  
-   Si tiene más sentido para facilitar la comunicación entre el Alemania y el programa, el entorno de tiempo de ejecución crea comparte el Alemania. Esto deja el SDM en un espacio de direcciones y el Alemania, el entorno de tiempo de ejecución y el programa en otro. Esto es típico de una DE que se implementa con un intérprete para ejecutar con scripts de idiomas.  
  
    > [!NOTE]
    >  Cómo se asocia el Alemania al programa es depende de la implementación. Comunicación entre el Alemania y el programa también es dependiente de la implementación.  
  
## <a name="implementation"></a>Implementación  
 Mediante programación, cuando el Administrador de sesión de depuración (SDM) recibe por primera vez el [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) objeto que representa el programa que se iniciará, llama a la [adjuntar](../../extensibility/debugger/reference/idebugprogram2-attach.md) método y pásele un [ IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) objeto, que es una versión posterior se utiliza para pasar eventos de depuración hacia el SDM. El `IDebugProgram2::Attach` método, a continuación, llama a la [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) método. Para obtener más información sobre cómo el SDM recibe el `IDebugProgram2` de la interfaz, vea [notificar el puerto](../../extensibility/debugger/notifying-the-port.md).  
  
 Si su Alemania deba ejecutarse en el mismo espacio de direcciones que el programa se está depurando, normalmente debido a la DE forma parte de un intérprete en ejecución de una secuencia de comandos, el `IDebugProgramNodeAttach2::OnAttach` método `S_FALSE`, que indica que ha completado el proceso de conexión.  
  
 Si, por otro lado, la DE se ejecuta en el espacio de direcciones de SDM, la `IDebugProgramNodeAttach2::OnAttach` método devuelve `S_OK` o [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) interfaz no está implementada en absoluto en la [IDebugProgramNode2 ](../../extensibility/debugger/reference/idebugprogramnode2.md) objeto asociado con el programa que se está depurando. En este caso, el [adjuntar](../../extensibility/debugger/reference/idebugengine2-attach.md) finalmente se llama el método para completar la operación de adjuntar.  
  
 En el último caso, debe llamar a la [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) método en el `IDebugProgram2` objeto que se pasó a la `IDebugEngine2::Attach` /método siguiente, el almacén de la `GUID` en el sistema local de objetos y devolver esto `GUID` cuando el `IDebugProgram2::GetProgramId` se llama al método en este objeto. El `GUID` se utiliza para identificar de forma única el programa a través de los distintos componentes de depuración.  
  
 Tenga en cuenta que en el caso de la `IDebugProgramNodeAttach2::OnAttach` método devolver `S_FALSE`, el `GUID` que se usará para el programa se pasa a ese método y es el `IDebugProgramNodeAttach2::OnAttach` método que establece el `GUID` en el objeto de programa local.  
  
 La DE se adjunta al programa y está listo para enviar los eventos de inicio.  
  
## <a name="see-also"></a>Vea también  
 [Conectar directamente a un programa](../../extensibility/debugger/attaching-directly-to-a-program.md)   
 [Notificar el puerto](../../extensibility/debugger/notifying-the-port.md)   
 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)   
 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [Adjuntar](../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Asociar](../../extensibility/debugger/reference/idebugengine2-attach.md)