---
title: "Asociar despu&#233;s de un lanzamiento | Microsoft Docs"
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
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Asociar despu&#233;s de un lanzamiento
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Una vez inicia un programa, la sesión de depuración está lista para asociar el motor de \(DE\) depuración programar dicho.  
  
## decisiones de diseño  
 Dado que la comunicación es más fácil dentro de un espacio de direcciones compartido, debe decidir si tiene más sentido para facilitar la comunicación entre la sesión de depuración y el OF, o entre el OF y el programa.  Elegir entre lo siguiente:  
  
-   Si tiene más sentido para facilitar la comunicación entre la sesión de depuración y el OF, la sesión de depuración participa el OF y dicho OF para asociar el programa.  Esto permite a la sesión de depuración y el OF conjuntamente en un espacio de direcciones, y el entorno de tiempo de ejecución y el programa conjuntamente en otro.  
  
-   Si tiene más sentido para facilitar la comunicación entre el OF y el programa, el entorno de tiempo de ejecución participa el OF.  Esto permite el SDM en un espacio de direcciones, y el OF, el entorno de tiempo de ejecución, y el programa juntos en otro.  Esto es habitual de un OF que se implemente con un intérprete para trabajar con lenguajes con scripts.  
  
    > [!NOTE]
    >  Cómo el OF asocia el programa es implementación\-dependiente.  La comunicación entre el OF y el programa también es implementación\-dependiente.  
  
## Implementación  
 Mediante programación, cuando el administrador de depuración de sesión \(SDM\) primero recibe el objeto de [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) que representa el programa que se arrancará, llama al método de [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md) , pasándole un objeto de [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) , que se utiliza posteriormente para devolver eventos de depuración al SDM.  Después el método `IDebugProgram2::Attach` llama al método [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md).  Para obtener más información sobre cómo el SDM recibe la interfaz de `IDebugProgram2` , vea [Notificar el puerto](../../extensibility/debugger/notifying-the-port.md).  
  
 Si el OF necesita ejecutar al mismo espacio de direcciones que el programa que se está depurando, normalmente porque el OF es parte de un intérprete que ejecuta un script, el método de `IDebugProgramNodeAttach2::OnAttach` devuelve `S_FALSE`, que indica que ha finalizado el proceso de asociar.  
  
 Si, por otro lado, el OF se ejecuta en el espacio de direcciones de SDM, el método de `IDebugProgramNodeAttach2::OnAttach` devuelve `S_OK` o la interfaz de [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) no se implementa en el objeto de [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) asociado al programa que se depura.  En este caso, el método de [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) se llama finalmente para completar la operación de asociar.  
  
 En este último caso, se debe llamar al método de [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) en el objeto de `IDebugProgram2` que se pasó al método de `IDebugEngine2::Attach` , almacena `GUID` en el objeto local del programa, y devuelve este `GUID` cuando el método de `IDebugProgram2::GetProgramId` posteriormente se llama en este objeto.  `GUID` se utiliza para identificar el programa únicamente los distintos componentes de depuración.  
  
 Observe que en el caso del método de `IDebugProgramNodeAttach2::OnAttach` que devuelve `S_FALSE`, `GUID` a utilizar para el programa se pasa al método y es el método de `IDebugProgramNodeAttach2::OnAttach` que establece `GUID` en el objeto local del programa.  
  
 El OF ahora se asocia al programa y listo para enviar cualquier evento startup.  
  
## Vea también  
 [Asociar directamente a un programa](../../extensibility/debugger/attaching-directly-to-a-program.md)   
 [Notificar el puerto](../../extensibility/debugger/notifying-the-port.md)   
 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)   
 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)