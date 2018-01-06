---
title: Asociar al programa | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debug engines, attaching to programs
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 75b532005bf4aeb471aa16ecfc6ac8ff508e3c7f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="attaching-to-the-program"></a>Asociar al programa
Después de haber registrado los programas con el puerto adecuado, debe asociar al depurador al programa que desea depurar.  
  
## <a name="choosing-how-to-attach"></a>Elegir cómo adjuntar  
 Hay tres formas en que el Administrador de sesión de depuración (SDM) intenta adjuntar al programa que se está depurando.  
  
1.  En los programas que se inician mediante el motor de depuración a través de la [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) método (típica de idiomas interpretados, por ejemplo), el SDM Obtiene la [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) de la interfaz de el [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) objeto asociado con el programa que se va a adjuntar a. Si puede obtener el SDM el `IDebugProgramNodeAttach2` el SDM, a continuación, llama a la interfaz, el [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) método. El `IDebugProgramNodeAttach2::OnAttach` método devuelve `S_OK` para indicar que no lo ha adjuntado al programa y que se pueden realizar otros intentos para adjuntar al programa.  
  
2.  Si puede obtener el SDM el [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md) interfaz desde el programa que se va a adjuntar a las llamadas SDM el [adjuntar](../../extensibility/debugger/reference/idebugprogramex2-attach.md) método. Este enfoque es típico de programas que se inicien de forma remota por el proveedor del puerto.  
  
3.  Si el programa no se puede conectar a través de la `IDebugProgramNodeAttach2::OnAttach` o `IDebugProgramEx2::Attach` métodos, el SDM carga el motor de depuración (si aún no está cargada) mediante una llamada a la `CoCreateInstance` función y, a continuación, llama el [adjuntar](../../extensibility/debugger/reference/idebugengine2-attach.md) método. Este enfoque es típico de programas iniciados localmente por un proveedor de puerto.  
  
     También es posible que un proveedor de puerto personalizado llamar a la `IDebugEngine2::Attach` método de implementación del proveedor de puerto personalizado de la `IDebugProgramEx2::Attach` método. En este caso, normalmente el proveedor del puerto personalizado inicia el motor de depuración en el equipo remoto.  
  
 Datos adjuntos se consigue cuando el Administrador de sesión de depuración (SDM) llama el [adjuntar](../../extensibility/debugger/reference/idebugengine2-attach.md) método.  
  
 Si ejecuta su Alemania en el mismo proceso que la aplicación va a depurar, debe implementar los métodos siguientes de [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md):  
  
-   [GetHostName](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md),  
  
-   [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)  
  
-   [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)  
  
 Después de la `IDebugEngine2::Attach` se llama al método, siga estos pasos en la implementación de la `IDebugEngine2::Attach` método:  
  
1.  Enviar una [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) objeto de evento para el SDM. Para obtener más información, consulte [enviar eventos](../../extensibility/debugger/sending-events.md).  
  
2.  Llame a la [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) método en el [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) objeto que se pasó a la `IDebugEngine2::Attach` método.  
  
     Esto devuelve un `GUID` que se usa para identificar el programa. El `GUID` deben almacenarse en el objeto que representa la variable local de programa a la DE y se debe devolver cuando la `IDebugProgram2::GetProgramId` método se llama en el `IDebugProgram2` interfaz.  
  
    > [!NOTE]
    >  Si implementa el `IDebugProgramNodeAttach2` de la interfaz, el programa `GUID` se pasa a la `IDebugProgramNodeAttach2::OnAttach` método. Esto `GUID` se usa para el programa `GUID` devuelto por la `IDebugProgram2::GetProgramId` método.  
  
3.  Enviar una [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) objeto de evento para notificar el SDM que la variable local `IDebugProgram2` objeto se creó para representar el sistema a la DE. Para obtener más información, consulte [enviar eventos](../../extensibility/debugger/sending-events.md).  
  
    > [!NOTE]
    >  Esto no es lo mismo `IDebugProgram2` objeto que se pasó a la `IDebugEngine2::Attach` método. Anteriormente pasado `IDebugProgram2` objeto es reconocido por el puerto solo y es un objeto independiente.  
  
## <a name="see-also"></a>Vea también  
 [Datos adjuntos basada en Inicio](../../extensibility/debugger/launch-based-attachment.md)   
 [El envío de eventos](../../extensibility/debugger/sending-events.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)   
 [Adjuntar](../../extensibility/debugger/reference/idebugprogramex2-attach.md)   
 [Asociar](../../extensibility/debugger/reference/idebugengine2-attach.md)