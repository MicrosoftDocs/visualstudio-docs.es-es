---
title: Iniciar un programa | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debug engines, launching
- programs, launching
ms.assetid: 6857e9c6-e44a-468a-afa4-f7c4a0b77844
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c3af2c1f571287a4a33c1dd57340e2a66197bd59
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51753959"
---
# <a name="launching-a-program"></a>Inicio de un programa
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Los usuarios que desean depurar un programa pueden presionar F5 para ejecutar al depurador desde el IDE. Esto inicia una serie de eventos producidos en última instancia en el IDE se conecta a un motor de depuración (DE), que a su vez está conectado o adjunta, al programa como se indica a continuación:  
  
1. El IDE llama primero el paquete del proyecto para obtener la configuración de depuración de proyecto activo de la solución. La configuración incluye el directorio de inicio, las variables de entorno, el puerto en que se ejecutará el programa y la DE usar para crear el programa, si se especifica. Estos valores se pasan en el paquete de depuración.  
  
2. Si se especifica a DE, el sistema operativo para iniciar el programa llama a la DE. Como consecuencia de iniciar el programa, se carga el entorno de tiempo de ejecución del programa. Por ejemplo, si se escribe un programa en MSIL, se invocará el common language runtime para ejecutar el programa.  
  
    O bien  
  
    Si no se especifica a DE, el puerto llama el sistema operativo para iniciar el programa, lo que hace que el entorno de tiempo de ejecución del programa que se cargue.  
  
   > [!NOTE]
   >  Si a DE se usa para iniciar un programa, es probable que se adjuntará al mismo DE al programa.  
  
3. Dependiendo de si el puerto o la DE inicia el programa, la DE o el entorno de tiempo de ejecución, a continuación, crea una descripción del programa o el nodo y notifica el puerto que se ejecuta el programa.  
  
   > [!NOTE]
   >  Se recomienda que el entorno de tiempo de ejecución crea el nodo de programa, porque el nodo de programa es una representación reducida de un programa que se puede depurar. No hay ninguna necesidad de cargar una completa DE solo para crear y registrar un nodo de programa. Si se ha diseñado la DE para ejecutarse en el proceso del IDE, pero ningún IDE está realmente se está ejecutando, debe haber un componente que se puede agregar un nodo de programa al puerto.  
  
   El programa recién creado, junto con todos los demás programas, relacionados con o no relacionados, inicia o adjuntados para desde el mismo IDE, crear una sesión de depuración.  
  
   Mediante programación, cuando el usuario primero presiona **F5**, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]del paquete de depuración llama al paquete de proyecto (que está asociado con el tipo de programa que se va a iniciar) a través de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> método, que a su vez se rellena un <xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2> estructura con la configuración de depuración del proyecto activo de la solución. Esta estructura se pasa al paquete de depuración mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A> método. El paquete de depuración, a continuación, crea el Administrador de sesión de depuración (SDM), que inicia el programa que se va a motores de depuración depurado y cualquier asociado.  
  
   Uno de los argumentos pasados al SDM es el GUID de la DE que se usará para iniciar el programa.  
  
   Si no lo es el GUID DE `GUID_NULL`, el SDM participa en la DE la creación y, a continuación, llama a su [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) método para iniciar el programa. Por ejemplo, si un programa está escrito en código nativo, a continuación, `IDebugEngineLaunch2::LaunchSuspended` llamará probablemente `CreateProcess` y `ResumeThread` (funciones de Win32) para ejecutar el programa.  
  
   Como consecuencia de iniciar el programa, se carga el entorno de tiempo de ejecución del programa. La DE o el entorno de tiempo de ejecución, a continuación, crea un [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) para describir el programa de la interfaz y pasa esta interfaz para [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) para notificar el puerto que el programa es está ejecutando.  
  
   Si `GUID_NULL` se pasa a continuación, el programa inicia el puerto. Una vez que se ejecuta el programa, el entorno de tiempo de ejecución crea un `IDebugProgramNode2` interfaz para describir el programa y lo pasa a `IDebugPortNotify2::AddProgramNode`. Así notifica el puerto que se ejecuta el programa. A continuación, el SDM adjunta el motor de depuración al programa en ejecución.  
  
## <a name="in-this-section"></a>En esta sección  
 [Notificación del puerto](../../extensibility/debugger/notifying-the-port.md)  
 Explica lo que sucede después de que se inicia un programa y se notifica el puerto.  
  
 [Asociación después de un lanzamiento](../../extensibility/debugger/attaching-after-a-launch.md)  
 Documentos cuando esté lista para adjuntar la DE que el programa de la sesión de depuración.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)  
 Contiene vínculos a diversas tareas de depuración, como iniciar un programa y evaluar expresiones.

