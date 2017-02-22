---
title: "Iniciar un programa | Microsoft Docs"
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
  - "motores de depuración, iniciar"
  - "programas, iniciar"
ms.assetid: 6857e9c6-e44a-468a-afa4-f7c4a0b77844
caps.latest.revision: 21
caps.handback.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
---
# Iniciar un programa
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Los usuarios que deseen depurar un programa pueden presionar F5 para ejecutar el depurador del IDE.  Esto inicia una serie de eventos que den lugar finalmente al IDE que conecta con un motor de depuración \(DE\), que a su vez está conectado, o asociar, programar como sigue:  
  
1.  Del IDE llama primero al paquete del proyecto para obtener los valores de depuración del proyecto de la solución activa.  Los valores incluyen el directorio inicial, las variables de entorno, el puerto en el que el programa se ejecutará, y el OF para crear el programa, si se especifica.  Estos valores se pasan al paquete de depuración.  
  
2.  Si se especifica un OF, el OF llama al sistema operativo para iniciar el programa.  Como resultado de iniciar el programa, el entorno en tiempo de ejecución del programa se carga.  Por ejemplo, si un programa se escribe en MSIL, Common Language Runtime se invocará para ejecutar el programa.  
  
     O bien  
  
     Si un OF no se especifica, el puerto llama al sistema operativo para iniciar el programa, que hace que el entorno en tiempo de ejecución del programa que se va a cargar.  
  
    > [!NOTE]
    >  Si un OF se utiliza para iniciar un programa, es probable que el mismo OF está adjunto al programa.  
  
3.  Dependiendo de si el OF o puerto arrancó el programa, el OF o el entorno de tiempo de ejecución después crea una descripción del nodo, o, y notifica al puerto se ejecuta el programa.  
  
    > [!NOTE]
    >  Se recomienda que el entorno de tiempo de ejecución crea el nodo del programa, porque el nodo del programa es una representación ligera de un programa que puede depurar.  No hay necesidad de cargar para buscar un OF completo solo para crear y registrar un nodo del programa.  Si el OF está diseñado para ejecutarse en curso del IDE, pero no el IDE ejecuta realmente, necesita ser un componente que puede agregar un nodo de programa al puerto.  
  
 El programa recién creado, junto con cualquier otro programa, relacionadas o sin relación, iniciará o adjunto de mismo IDE, crea una sesión de depuración.  
  
 Mediante programación, cuando el usuario presiona primero **F5**, el paquete de depuración de los vsprvs llama al paquete del proyecto \(que está asociado al tipo de programa que se iniciará\) con el método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> , que a su vez completa una estructura de<xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2> con la depuración del proyecto de la solución activa.  Esta estructura se pasa al paquete de depuración con una llamada al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A> .  El paquete de depuración se crea una instancia del administrador \(SDM\) de depuración de sesión, que inicia el programa que se depura y cualquier motor asociado de depuración.  
  
 Uno de los argumentos pasados al SDM es un GUID de que se utilizará para iniciar el programa.  
  
 Si el OF GUID no es `GUID_NULL`, el SDM participa el OF, y después llama a su método de [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) para iniciar el programa.  Por ejemplo, si un programa está escrita en código nativo, después `IDebugEngineLaunch2::LaunchSuspended` llamará probablemente `CreateProcess` y `ResumeThread` \(funciones de Win32\) para ejecutar el programa.  
  
 Como resultado de iniciar el programa, el entorno en tiempo de ejecución del programa se carga.  El OF o el entorno de tiempo de ejecución después crear una interfaz de [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) para describir el programa y pasa esta interfaz a [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) para notificar al puerto se ejecuta el programa.  
  
 Si se pasa `GUID_NULL` , el puerto inicia el programa.  Una vez que el programa se está ejecutando, el entorno de tiempo de ejecución crea una interfaz de `IDebugProgramNode2` para describir el programa y pasarlo a `IDebugPortNotify2::AddProgramNode`.  Esto notifica al puerto se ejecuta el programa.  El SDM asocia el motor de depuración al programa en ejecución.  
  
## En esta sección  
 [Notificar el puerto](../../extensibility/debugger/notifying-the-port.md)  
 Explica lo que ocurre una vez iniciado un programa y se notifica al puerto.  
  
 [Asociar después de un lanzamiento](../../extensibility/debugger/attaching-after-a-launch.md)  
 Documentos cuando la sesión de depuración está lista para adjuntar el DE el programa.  
  
## Secciones relacionadas  
 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)  
 Contiene vínculos a las diferentes tareas de depuración, como iniciar un programa y evaluación de expresiones.