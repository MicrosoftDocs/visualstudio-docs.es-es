---
title: Lanzamiento de un programa ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- programs, launching
ms.assetid: 6857e9c6-e44a-468a-afa4-f7c4a0b77844
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf638e0c96c7df1de2650260427a972a07efce23
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738479"
---
# <a name="launch-a-program"></a>Iniciar un programa
Los usuarios que desean depurar un programa pueden presionar **F5** para ejecutar el depurador desde el IDE. Esto comienza una serie de eventos que en última instancia dan lugar a que el IDE se conecte a un motor de depuración (DE), que a su vez está conectado, o conectado, al programa de la siguiente manera:

1. El IDE llama primero al paquete de proyecto para obtener la configuración de depuración de proyecto activa de la solución. La configuración incluye el directorio inicial, las variables de entorno, el puerto en el que se ejecutará el programa y la DE que se utilizará para crear el programa, si se especifica. Esta configuración se pasa al paquete de depuración.

2. Si se especifica un DE, el DE llama al sistema operativo para iniciar el programa. Como consecuencia del lanzamiento del programa, se carga el entorno en tiempo de ejecución del programa. Por ejemplo, si un programa se escribe en MSIL, se invocará Common Language Runtime para ejecutar el programa.

    o bien

    Si no se especifica un DE, el puerto llama al sistema operativo para iniciar el programa, lo que hace que el entorno de tiempo de ejecución del programa se cargue.

   > [!NOTE]
   > Si se utiliza un DE para iniciar un programa, es probable que se adjunte el mismo DE al programa.

3. Dependiendo de si el DE o el puerto iniciaron el programa, el DE o el entorno en tiempo de ejecución crea una descripción del programa, o nodo, y notifica al puerto que el programa se está ejecutando.

   > [!NOTE]
   > Se recomienda que el entorno en tiempo de ejecución cree el nodo de programa, ya que el nodo de programa es una representación ligera de un programa que se puede depurar. No es necesario cargar un DE completo solo para crear y registrar un nodo de programa. Si la DE está diseñada para ejecutarse en el proceso del IDE, pero no se está ejecutando ningún IDE, debe haber un componente que pueda agregar un nodo de programa al puerto.

   El programa recién creado, junto con cualquier otro programa, relacionado o no relacionado, iniciado o asociado desde el mismo IDE, componen una sesión de depuración.

   Mediante programación, cuando el usuario [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]presiona por primera vez **F5**, el paquete de depuración de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> 's llama al paquete <xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2> de proyecto (que está asociado con el tipo de programa que se inicia) a través del método, que a su vez rellena una estructura con la configuración de depuración del proyecto activo de la solución. Esta estructura se devuelve al paquete de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A> depuración a través de una llamada al método. A continuación, el paquete de depuración crea una instancia del administrador de depuración de sesión (SDM), que inicia el programa que se está depurando y los motores de depuración asociados.

   Uno de los argumentos pasados al SDM es el GUID de la DE que se usará para iniciar el programa.

   Si el GUID `GUID_NULL`DE no lo es , el SDM crea automáticamente el DE y, a continuación, llama a su [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) método para iniciar el programa. Por ejemplo, si un programa está `IDebugEngineLaunch2::LaunchSuspended` escrito `CreateProcess` en `ResumeThread` código nativo, probablemente llamará y (funciones Win32) para ejecutar el programa.

   Como consecuencia del lanzamiento del programa, se carga el entorno de tiempo de ejecución del programa. El DE o el entorno en tiempo de ejecución, a continuación, crea un [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) interfaz para describir el programa y pasa esta interfaz a [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) para notificar al puerto que el programa se está ejecutando.

   Si `GUID_NULL` se pasa, el puerto inicia el programa. Una vez que el programa se está `IDebugProgramNode2` ejecutando, el entorno en `IDebugPortNotify2::AddProgramNode`tiempo de ejecución crea una interfaz para describir el programa y lo pasa a . Esto notifica al puerto que el programa se está ejecutando. A continuación, el SDM asocia el motor de depuración al programa en ejecución.

## <a name="in-this-section"></a>En esta sección
 [Notificar al puerto](../../extensibility/debugger/notifying-the-port.md) Explica lo que sucede después de que se inicia un programa y se notifica al puerto.

 [Adjuntar después de un lanzamiento](../../extensibility/debugger/attaching-after-a-launch.md) Documentos cuando la sesión de depuración está lista para adjuntar el DE al programa.

## <a name="related-sections"></a>Secciones relacionadas
 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md) Contiene vínculos a varias tareas de depuración, como iniciar un programa y evaluar expresiones.
