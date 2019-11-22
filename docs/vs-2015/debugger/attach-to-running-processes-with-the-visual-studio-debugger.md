---
title: Attach to Running Processes with the Debugger | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.processes.attach
- vs.debug.process
- vs.debug.programs
- vs.debug.detaching
- vs.debug.processes
- vs.debug.error.attach
- vs.debug.remotemachine
dev_langs:
- C++
- CSharp
- FSharp
- VB
- c++
helpviewer_keywords:
- remote debugging, attaching to programs
- processes, attaching to running processes
- Attach to Process dialog box
- debugging [Visual Studio], attaching to processes
- debugger, processes
ms.assetid: 27900e58-090c-4211-a309-b3e1496d5824
caps.latest.revision: 62
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 03cd890802e5563ce2daeb78438c56f4452d74f0
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299509"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Crear asociaciones con procesos en ejecución con el depurador de Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede asociar el depurador de Visual Studio a un proceso en ejecución en un equipo local o remoto. After the process is running, click **Debug / Attach to Process** (or press **CTRL+ALT+P**) to open the **Attach to Process** dialog box.

You can use this capability to debug apps that are running on a local or remote computer, debug multiple processes simultaneously, or debug an application that was not created in Visual Studio. It is often useful when you want to debug an app, but (for whatever reason) you did not start the app from Visual Studio with the debugger attached. For example, if you are running the app without the debugger and hit an exception, you might then attach to the process running the app to begin debugging.

> [!TIP]
> Not sure whether you need to use **Attach to Process** for your debugging scenario? See [Common debugging scenarios](#BKMK_Scenarios). If you want to debug ASP.NET applications that have been deployed to IIS, see [Remote Debugging ASP.NET on a remote IIS computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

## <a name="BKMK_Attach_to_a_running_process"></a> Attach to a running process on the local machine
 In order to attach to a process, you must know the name of the process (see [Common debugging scenarios](#BKMK_Scenarios) for a few common process names).

1. In Visual Studio, select **Debug / Attach to Process** (or press **CTRL+ALT+P**).

2. En el cuadro de diálogo **Asociar al proceso** , seleccione el programa que desea asociar en la lista **Procesos disponibles** .

     To quickly select the process you want, type the first letter of the process name. If you don't know the process name, see [Common debugging scenarios](#BKMK_Scenarios).

     ![DBG_Basics_Attach_To_Process](../debugger/media/dbg-basics-attach-to-process.png "DBG_Basics_Attach_To_Process")

     Si el proceso se ejecuta con una cuenta de usuario diferente, active la casilla **Mostrar los procesos de todos los usuarios** .

3. En el cuadro **Asociar a** , asegúrese de que aparece el tipo de código que quiere depurar. El valor predeterminado **Automático** intenta determinar qué tipo de código desea depurar. Para establecer el tipo de código manualmente, haga lo siguiente:

    1. En el cuadro de diálogo **Asociar a** , haga clic en **Seleccionar**.

    2. En el cuadro de diálogo **Seleccionar tipo de código** , haga clic en **Depurar estos tipos de código** y seleccione los tipos que va a depurar.

    3. Haga clic en **Aceptar**.

4. Haga clic en **Adjuntar**.

## <a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> Asociar a un proceso en un equipo remoto
 In order to attach to a process, you must know the name of the process (see [Common debugging scenarios](#BKMK_Scenarios) for a few common process names). For more complete guidance for ASP.NET apps that have been deployed to IIS, see [Remote Debugging ASP.NET on a remote IIS computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). En el caso de las demás aplicaciones, encontrará el nombre del proceso en el Administrador de tareas.

 En el cuadro de diálogo **Asociar al proceso** , puede seleccionar otro equipo configurado para la depuración remota. For more information, see [Remote Debugging](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c). Cuando se ha seleccionado un equipo remoto, se puede consultar una lista con los procesos disponibles que se están ejecutando en dicho equipo y establecer una asociación con uno o varios procesos para llevar a cabo la depuración.

 **To select a remote computer:**

1. In Visual Studio, select **Debug / Attach to Process** (or press **CTRL+ALT+P**).

2. En el cuadro **Asociar al proceso** , seleccione el tipo de conexión adecuado en la lista **Transporte** . **Valor predeterminado** es la configuración correcta en la mayoría de los casos.

   La configuración de **Transporte** se conserva entre las sesiones de depuración.

3. Utilice el cuadro de lista **Calificador** para elegir el nombre del equipo remoto mediante uno de los métodos siguientes:

   1. Escriba el nombre en el cuadro de lista **Calificador** .

      > [!NOTE]
      > If, in later steps, you can't connect using the remote computer name, use the IP address. (The port number may appear automatically after selecting the process. You can also enter it manually. In the illustration below, 4020 is the default port for the remote debugger.)

   2. Haga clic en la flecha desplegable del cuadro de lista **Calificador** y seleccione el nombre del equipo en la lista desplegable.

   3. Click the **Find** button next to the **Qualifier** list to open the **Select Remote Debugger Connection** dialog box. El cuadro **Seleccionar conexión del depurador remoto** muestra todos los dispositivos que se encuentran en su subred local, y cualquier dispositivo conectado directamente al equipo mediante un cable Ethernet. Haga clic en el equipo o el dispositivo que desee y, a continuación, haga clic en **Seleccionar**.

      La configuración de **Calificador** sólo se conserva entre las sesiones de depuración si se produce una conexión de depuración correcta con ese calificador.

4. Haga clic en **Actualizar**.

     La lista **Procesos disponibles** aparecerá automáticamente al abrir el cuadro de diálogo **Procesos** . Los procesos se pueden iniciar y detener en segundo plano mientras el cuadro de diálogo está abierto. Sin embargo, el contenido no siempre estará actualizado. Es posible actualizar la lista en cualquier momento y ver los procesos en curso haciendo clic en **Actualizar**.

5. En el cuadro de diálogo **Asociar al proceso** , seleccione el programa que desea asociar en la lista **Procesos disponibles** .

    Si el proceso se ejecuta con una cuenta de usuario diferente, active la casilla **Mostrar los procesos de todos los usuarios** .

6. Haga clic en **Adjuntar**.

## <a name="additional-info"></a>Additional info

Puede tener asociados varios programas mientras realiza la depuración, pero sólo un programa estará activo en el depurador en cada momento. Puede establecer el programa activo en la barra de herramientas **Ubicación de depuración** o en la ventana **Procesos** . Para obtener más información, vea [Cómo: Establecer el programa actual](https://msdn.microsoft.com/7e1d7fa5-0e40-44cf-8c41-d3dba31c969e).

Si intenta asociar a un proceso que pertenece a una cuenta de usuario que no es de confianza, aparecerá un cuadro de diálogo de confirmación con una advertencia de seguridad. Para obtener más información, consulte [advertencia de seguridad: Adjuntar a un proceso que pertenezca a un usuario de confianza puede ser peligroso. Si la información siguiente le resulta sospechosa o no está seguro de su procedencia, no la adjunte a este proceso](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015).

En algunos casos, al depurar en una sesión de Escritorio remoto (Terminal Services), en la lista **Procesos disponibles** no aparecerán todos los procesos disponibles. Si se ejecuta Visual Studio como usuario que tiene una cuenta de usuario limitada, la lista **Procesos disponibles** no mostrará los procesos que se estén ejecutando en la sesión 0, la cual se usa para los servicios y otros procesos de servidor, incluido w3wp.exe. Para resolver el problema, ejecute [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] con una cuenta de administrador o ejecute [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] desde la consola de servidor en lugar de una sesión de Terminal Services. Si ninguna de estas dos soluciones es posible, existe una tercera opción que consiste en asociar al proceso mediante la ejecución de `vsjitdebugger.exe -p` *ProcessId* en la línea de comandos de Windows. Puede determinar el identificador de proceso mediante tlist.exe. Para obtener el archivo tlist.exe, descargue e instale las Herramientas de depuración para Windows, disponibles en  [Descargas de WDK y WinDbg](https://go.microsoft.com/fwlink/?LinkId=168279).

## <a name="BKMK_Scenarios"></a> Common debugging scenarios

To help you identify whether you need to use **Attach to process** and what process to attach to, a few common debugging scenarios are shown here (the list is not exhaustive). Where more instructions are available, we provide links.

For some app types (like Windows Store apps), you don't attach directly to a process name, but use the **Debug Installed App Package** menu option instead (see table).

> [!NOTE]
> For information about basic debugging in Visual Studio, see [Getting started with the debugger](../debugger/getting-started-with-the-debugger.md).

|Escenario|Debug Method|Nombre del proceso|Notes and Links|
|-|-|-|-|
|Debug a managed or native app on the local machine|Use attach to process or [standard debugging](../debugger/getting-started-with-the-debugger.md)|*appname*.exe|To quickly access the dialog box, use **CTRL+ALT+P** and then type the first letter of the process name.|
|Debug ASP.NET apps on the local machine after starting the app without the debugger|Use attach to process|iiexpress.exe|This may be helpful to make your app load faster, such as (for example) when profiling. |
|Remote debug ASP.NET 4 or 4.5 on an IIS server|Use remote tools and attach to process|w3wp.exe|See [Remote Debugging ASP.NET on a remote IIS computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Remote debug ASP.NET Core on an IIS server|Use remote tools and attach to process|dnx.exe|For app deployment, see [Publish to IIS](https://docs.asp.net/en/latest/publishing/iis.html). For debugging, see [Remote Debugging ASP.NET on a remote IIS computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Debug other supported app types on a server process|Use remote tools (if server is remote) and attach to process|iexplore.exe or other processes|If necessary, use Task Manager to help identify the process. See [Remote Debugging](../debugger/remote-debugging.md) and later sections in this topic|
|Remote debug a Windows desktop app|Remote Tools and F5|N/D| See [Remote Debugging](../debugger/remote-debugging.md)|
|Remote debug a Windows Universal (UWP), OneCore, HoloLens, or IoT app|Depurar paquete de aplicaciones instalado|N/D|Use **Debug / Other Debug Targets / Debug Installed App Package** instead of **Attach to process**|
|Debug a Windows Universal (UWP), OneCore, HoloLens, or IoT app that you didn't start from Visual Studio|Depurar paquete de aplicaciones instalado|N/D|Use **Debug / Other Debug Targets / Debug Installed App Package** instead of **Attach to process**|

> [!WARNING]
> Para asociar a una aplicación universal de Windows escrita en JavaScript, primero debe habilitar la depuración de la aplicación. Vea [Attach the debugger](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md#BKMK_Attach_the_debugger) en el Centro de desarrollo de Windows.

> [!NOTE]
> Para que el depurador se asocie al código escrito en C++, el código debe emitir `DebuggableAttribute`. Puede agregar este atributo automáticamente al código vinculando con la opción [/ASSEMBLYDEBUG](https://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982) del vinculador.

## <a name="what-debugger-features-can-i-use"></a>What debugger features can I use?

To use the full features of the Visual Studio debugger (like hitting breakpoints) when attaching to a process, the executable must exactly match your local source and symbols (that is, the debugger must be able to load the correct [symbol (.pbd) files](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)). By default, this requires a debug build.

For remote debugging scenarios, you must have the source code (or a copy of the source code) already open in Visual Studio. The compiled app binaries on the remote machine must come from the same build as on the local machine.

In some local debugging scenarios, you can debug in Visual Studio with no access to the source if the correct symbol files are present with the app (by default, this requires a debug build). For more info, see [Specify Symbol and Source Files](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="BKMK_Troubleshoot_attach_errors"></a> Solucionar problemas de errores de asociación
 Cuando el depurador se asocia a un proceso en ejecución, el proceso puede contener uno o varios tipos de código. Los tipos de código a los que se puede asociar el depurador se muestran y seleccionan en el cuadro de diálogo **Seleccionar tipo de código** .

 A veces, el depurador puede asociarse correctamente a un tipo de código, pero no a otro. Esto puede ocurrir cuando se intenta asociar el depurador a un proceso que está ejecutándose en un equipo remoto. Puede que el equipo remoto tenga instalados los componentes de depuración remota para algunos tipos de código, pero no para otros. También puede ocurrir al intentar asociar el depurador a dos o varios procesos para realizar una depuración directa de la base de datos. La depuración de SQL sólo admite la asociación a un único proceso.

 Si el depurador logra asociarse a algunos tipos de código, pero no a todos, aparecerá un mensaje en el que se identifican los tipos sin asociar:

 Si el depurador se asocia correctamente a un tipo de código por lo menos, podrá reanudar la depuración del proceso. Sólo podrá depurar los tipos de código que se hayan asociado correctamente. El mensaje de ejemplo anterior indica que el tipo de código de script no se ha asociado correctamente. Por lo tanto, no podrá depurar código de script dentro del proceso. El código de script del proceso seguirá ejecutándose, pero no se podrán establecer puntos de interrupción, ni se podrán ver los datos, ni se podrá realizar ninguna otra operación de depuración en el script.

 Si desea obtener información más detallada sobre el motivo por el que el depurador no se ha asociado correctamente a un tipo de código, puede intentar asociarlo de nuevo con ese tipo de código exclusivamente.

 **To obtain specific information about why a code type failed to attach**

1. Desasocie el proceso. En el menú **Depurar** , haga clic en **Desasociar todo**.

2. Vuelva a asociar el proceso, pero seleccionando un único tipo de código.

   1. En el cuadro de diálogo **Asociar al proceso** , seleccione el proceso en la lista **Procesos disponibles** .

   2. Haga clic en **Seleccionar**.

   3. En el cuadro de diálogo **Seleccionar tipo de código** , seleccione **Depurar estos tipos de código** y el tipo de código que no se haya asociado correctamente. Borre cualquier otro código.

   4. Haga clic en **Aceptar**. El cuadro de diálogo **Seleccionar tipo de código** se cierra.

   5. En el cuadro de diálogo **Asociar al proceso** , haga clic en **Asociar**.

      Esta vez se producirá un error en todo el proceso de asociación y aparecerá un mensaje de error específico.

## <a name="see-also"></a>Vea también
 [Debug Multiple Processes](../debugger/debug-multiple-processes.md) [Just-In-Time Debugging](../debugger/just-in-time-debugging-in-visual-studio.md) [Remote Debugging](../debugger/remote-debugging.md)
