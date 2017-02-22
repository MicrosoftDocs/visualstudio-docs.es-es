---
title: "Asociar al programa | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "motores de depuración, asociar a programas"
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Asociar al programa
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Después de haber registrado programas con el puerto adecuado, debe asociar el depurador al programa que desea depurar.  
  
## Elegir Cómo para adjuntar  
 Hay tres maneras en las que el administrador de depuración de sesión \(SDM\) intenta asociar el programa que se depura.  
  
1.  Para los programas que son que el motor de depuración con el método de [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) \(típico de lenguajes y, por ejemplo\), el SDM obtiene la interfaz de [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) del objeto de [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) asociado al programa que se está adjunto a.  Si el SDM puede obtener la interfaz de `IDebugProgramNodeAttach2` , el SDM después llama al método de [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) .  El método de `IDebugProgramNodeAttach2::OnAttach` devuelve `S_OK` para indicar que no adjuntó el programa y que otros intentos se pueden crear para asociar el programa.  
  
2.  Si el SDM puede obtener la interfaz de [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md) del programa que se está adjunto a, el SDM llama al método de [Attach](../../extensibility/debugger/reference/idebugprogramex2-attach.md) .  Este enfoque es típico para programas iniciadas remotamente el proveedor de puerto.  
  
3.  Si el programa no se puede asociar con los métodos de `IDebugProgramNodeAttach2::OnAttach` o de `IDebugProgramEx2::Attach` , el SDM carga el motor de depuración \(si aún no está cargado\) llamando a la función de `CoCreateInstance` y después llamar al método de [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) .  Este enfoque es común para los programas que localmente por un proveedor de puerto.  
  
     También es posible que un proveedor de puerto llame al método de `IDebugEngine2::Attach` en la implementación personalizada del proveedor de puerto del método de `IDebugProgramEx2::Attach` .  Normalmente en este caso, el proveedor de puerto inicia el motor de depuración en el equipo remoto.  
  
 Se alcanzan los datos adjuntos al administrador de depuración de sesión \(SDM\) llama al método de [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) .  
  
 Si ejecuta el OF en el mismo proceso que la aplicación para depurar, debe implementar los métodos siguientes de [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md):  
  
-   [GetHostName](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md),  
  
-   [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)  
  
-   [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)  
  
 Después de llamar al método de `IDebugEngine2::Attach` , siga estos pasos en la implementación del método de `IDebugEngine2::Attach` :  
  
1.  Enviar un objeto de evento de [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) al SDM.  Para obtener más información, vea [Enviar eventos](../../extensibility/debugger/sending-events.md).  
  
2.  Llame al método de [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) en el objeto de [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) que se pasó al método de `IDebugEngine2::Attach` .  
  
     el devuelve `GUID` que se utiliza para identificar el programa.  `GUID` debe almacenarse en el objeto que representa el programa local al OF, y debe devolver cuando el método de `IDebugProgram2::GetProgramId` se llama en la interfaz de `IDebugProgram2` .  
  
    > [!NOTE]
    >  Si implementa la interfaz de `IDebugProgramNodeAttach2` , `GUID` de programa se pasa al método de `IDebugProgramNodeAttach2::OnAttach` .  Este `GUID` se utiliza para `GUID` de programa devuelto por el método de `IDebugProgram2::GetProgramId` .  
  
3.  Enviar un objeto de evento de [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) para notificar al SDM que el objeto local de `IDebugProgram2` se creó para representar el programa se OF.  Para obtener información detallada, vea [Enviar eventos](../../extensibility/debugger/sending-events.md).  
  
    > [!NOTE]
    >  Éste no es el mismo objeto de `IDebugProgram2` que se pasó al método de `IDebugEngine2::Attach` .  El objeto previamente último de `IDebugProgram2` es reconocido por el puerto sólo y es un objeto independiente.  
  
## Vea también  
 [Datos adjuntos basada en el inicio](../../extensibility/debugger/launch-based-attachment.md)   
 [Enviar eventos](../../extensibility/debugger/sending-events.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)   
 [Attach](../../extensibility/debugger/reference/idebugprogramex2-attach.md)   
 [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)