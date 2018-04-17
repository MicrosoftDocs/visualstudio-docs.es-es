---
title: Ejecutar un programa | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- programs, launching
ms.assetid: 6857e9c6-e44a-468a-afa4-f7c4a0b77844
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 714d751e9855b5567bf76ccd902fada727e14ba1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="launching-a-program"></a>Ejecutar un programa
Los usuarios que van a depurar un programa pueden presionar F5 para ejecutar al depurador desde el IDE. Esto inicia una serie de eventos que finalmente se en el IDE al conectar a un motor de depuración (Alemania), que a su vez esté conectado o adjunta, al programa como sigue:  
  
1.  El IDE llama primero el paquete del proyecto para obtener configuración de depuración de proyecto activo de la solución. La configuración incluye el directorio de inicio, las variables de entorno, el puerto en el que se ejecutará el programa y la DE usar para crear el programa, si se especifica. Estos valores se pasan al paquete de depuración.  
  
2.  Si se especifica un Alemania, la DE llama el sistema operativo para iniciar el programa. Como consecuencia de ejecutar el programa, se carga el entorno en tiempo de ejecución del programa. Por ejemplo, si un programa está escrito en MSIL, common language runtime se invocará para ejecutar el programa.  
  
     -o bien-  
  
     Si no se especifica un Alemania, el puerto llama el sistema operativo para iniciar el programa, lo que produce el entorno en tiempo de ejecución del programa que se va a cargar.  
  
    > [!NOTE]
    >  Si un Alemania se usa para iniciar un programa, es probable que se adjuntará al mismo DE al programa.  
  
3.  Dependiendo de si el puerto o la DE inicia el programa, la DE o el entorno de tiempo de ejecución, a continuación, crea una descripción del programa o el nodo y notifica el puerto que se ejecuta el programa.  
  
    > [!NOTE]
    >  Se recomienda que el entorno de tiempo de ejecución crea el nodo de programa, porque el nodo de programa es una representación reducida de un programa que se puede depurar. No es necesario para cargar un completo DE simplemente para crear y registrar un nodo de programa. Si el Alemania está diseñado para ejecutarse en el proceso del IDE, pero no IDE está realmente se está ejecutando, debe haber un componente que puede agregar un nodo de programa al puerto.  
  
 El programa recién creado, junto con todos los demás programas, relacionados con o no relacionados, inicia o adjuntados al desde el mismo IDE, crear una sesión de depuración.  
  
 Mediante programación, cuando el usuario primero presiona **F5**, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]del paquete de depuración llama el paquete del proyecto (que está asociado con el tipo de programa que se va a iniciar) a través de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> método, que a su vez rellena un <xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2> estructura con la configuración de depuración del proyecto activo de la solución. Esta estructura se pasa hacia el paquete de depuración mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A> método. El paquete de depuración, a continuación, crea el Administrador de sesión de depuración (SDM), que inicia el programa que se va a motores de depuración depurado y cualquier asociado.  
  
 Uno de los argumentos pasados a la SDM es el GUID de la DE que se usará para iniciar el programa.  
  
 Si no lo es el GUID DE `GUID_NULL`, el SDM participa en la DE la creación y, a continuación, llama a su [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) método para iniciar el programa. Por ejemplo, si un programa está escrito en código nativo, a continuación, `IDebugEngineLaunch2::LaunchSuspended` probablemente se llamará `CreateProcess` y `ResumeThread` (funciones de Win32) para ejecutar el programa.  
  
 Como consecuencia de ejecutar el programa, se carga el entorno en tiempo de ejecución del programa. La DE o el entorno de tiempo de ejecución, a continuación, crea un [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) para describir el programa de interfaz y pasa esta interfaz para [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) para notificar el puerto que el programa en ejecución.  
  
 Si `GUID_NULL` se pasa, a continuación, el puerto inicia el programa. Una vez que se ejecuta el programa, el entorno de tiempo de ejecución crea un `IDebugProgramNode2` interfaz para describir el programa y lo pasa a `IDebugPortNotify2::AddProgramNode`. Indica el puerto que se ejecuta el programa. A continuación, el SDM asocia el motor de depuración para el programa en ejecución.  
  
## <a name="in-this-section"></a>En esta sección  
 [Notificación del puerto](../../extensibility/debugger/notifying-the-port.md)  
 Explica lo que ocurre cuando se inicia un programa y se notifica el puerto.  
  
 [Asociación después de un lanzamiento](../../extensibility/debugger/attaching-after-a-launch.md)  
 Documentos cuando esté lista para adjuntar el Alemania al programa de la sesión de depuración.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)  
 Contiene vínculos a varias tareas de depuración, como iniciar un programa y la evaluación de expresiones.