---
title: Adjuntar después de un inicio | Microsoft Docs
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
ms.openlocfilehash: 693cf6d746f51862415f2f30e46d48a998047f14
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843326"
---
# <a name="attaching-after-a-launch"></a>Asociación tras el inicio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Una vez iniciado el programa, la sesión de depuración está lista para adjuntar el motor DE depuración (DE) a dicho programa.  
  
## <a name="design-decisions"></a>Decisiones de diseño  
 Dado que la comunicación es más fácil dentro de un espacio de direcciones compartidas, debe decidir si tiene más sentido facilitar la comunicación entre la sesión de depuración y el DE, o entre el y el programa. Elija entre lo siguiente:  
  
- Si tiene más sentido facilitar la comunicación entre la sesión DE depuración y el DE, la sesión de depuración cocreará y le pedirá que se adjunte al programa. Esto deja la sesión de depuración y se combina en un espacio de direcciones, y el entorno y el programa en tiempo de ejecución juntos en otro.  
  
- Si tiene más sentido facilitar la comunicación entre el y el programa, el entorno de tiempo de ejecución crea de forma conjunta el DE. Esto deja el SDM en un espacio de direcciones y el DE, el entorno en tiempo de ejecución y el programa juntos en otro. Esto es típico de un DE que se implementa con un intérprete para ejecutar lenguajes de scripts.  
  
    > [!NOTE]
    > Cómo el DE se asocia al programa depende de la implementación. La comunicación entre el y el programa también depende de la implementación.  
  
## <a name="implementation"></a>Implementación  
 Mediante programación, cuando el administrador de depuración de sesión (SDM) recibe primero el objeto [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) que representa el programa que se va a iniciar, llama al método [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md) , pasándole un objeto [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) , que se usa posteriormente para pasar los eventos de depuración de vuelta al SDM. `IDebugProgram2::Attach`Después, el método llama al método [AutoAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) . Para obtener más información sobre cómo recibe el SDM la `IDebugProgram2` interfaz, consulte [notificar el puerto](../../extensibility/debugger/notifying-the-port.md).  
  
 Si su DE tiene que ejecutarse en el mismo espacio de direcciones que el programa que se está depurando, normalmente porque el DE forma parte de un intérprete que ejecuta un script, el `IDebugProgramNodeAttach2::OnAttach` método devuelve `S_FALSE` , lo que indica que ha completado el proceso de asociación.  
  
 Por otra parte, si de se ejecuta en el espacio de direcciones del SDM, el `IDebugProgramNodeAttach2::OnAttach` método devuelve `S_OK` o la interfaz [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) no se implementa en absoluto en el objeto [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) asociado al programa que se está depurando. En este caso, se llama al método [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) para completar la operación de adjuntar.  
  
 En el último caso, debe llamar al método [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) en el `IDebugProgram2` objeto que se pasó al `IDebugEngine2::Attach` método, almacenar el `GUID` en el objeto de programa local y devolverlo `GUID` cuando `IDebugProgram2::GetProgramId` se llama al método posteriormente en este objeto. `GUID`Se utiliza para identificar el programa de forma exclusiva en los distintos componentes de depuración.  
  
 Tenga en cuenta que en el caso del `IDebugProgramNodeAttach2::OnAttach` método que devuelve `S_FALSE` , el que se `GUID` va a utilizar para el programa se pasa a ese método y es el `IDebugProgramNodeAttach2::OnAttach` método que establece `GUID` en el objeto de programa local.  
  
 El DE ahora se adjunta al programa y está listo para enviar los eventos DE Inicio.  
  
## <a name="see-also"></a>Consulte también  
 [Adjuntar directamente a un programa](../../extensibility/debugger/attaching-directly-to-a-program.md)   
 [Notificación del puerto](../../extensibility/debugger/notifying-the-port.md)   
 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)   
 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [Incluir](../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Conectar](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Adjuntar](../../extensibility/debugger/reference/idebugengine2-attach.md)
