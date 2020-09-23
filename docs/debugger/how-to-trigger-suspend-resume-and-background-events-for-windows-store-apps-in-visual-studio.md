---
title: Desencadenamiento de eventos de suspensión, reanudación y en segundo plano al depurar UWP
ms.date: 01/16/2018
ms.topic: how-to
f1_keywords:
- vs.debug.error.background_task_activate_failure
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 5cbdfb443d07b01f4de6f43fb98103339566cde2
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808199"
---
# <a name="how-to-trigger-suspend-resume-and-background-events-while-debugging-uwp-apps-in-visual-studio"></a>Desencadenamiento de eventos de suspensión, reanudación y en segundo plano al depurar aplicaciones para UWP en Visual Studio

Cuando no estás depurando, la **Administración de la duración de los procesos** (PLM) de Windows controla el estado de ejecución de la aplicación, es decir, inicia, suspende, reanuda y finaliza la aplicación en respuesta a las acciones del usuario y al estado del dispositivo. Mientras depuras, Windows deshabilita estos eventos de activación. En este tema se describe cómo activar estos eventos en el depurador.

También se describe cómo depurar **tareas en segundo plano**. Las tareas en segundo plano permiten realizar algunas operaciones en un proceso de segundo plano, aunque la aplicación no esté en ejecución. Puedes utilizar el depurador para poner la aplicación en modo de depuración y, sin iniciar la interfaz de usuario, iniciar y depurar la tarea en segundo plano.

Para más información sobre la administración de la duración de los procesos y las tareas en segundo plano, consulte [Inicio, reanudación y tareas en segundo plano](/windows/uwp/launch-resume/index).

## <a name="trigger-process-lifetime-management-events"></a><a name="BKMK_Trigger_Process_Lifecycle_Management_events"></a> Desencadenar eventos de la Administración de la duración de los procesos
 Windows puede suspender la aplicación cuando el usuario cambia a otra aplicación o cuando Windows entra en estado de baja energía. Puedes responder al evento `Suspending` para guardar los datos pertinentes de la aplicación y del usuario en el almacenamiento persistente, y para liberar recursos. Cuando una aplicación se reanuda del estado **suspendido** , entra en el estado de **ejecución** y sigue desde el punto donde se suspendió. Puedes responder al evento `Resuming` para restaurar o actualizar el estado de la aplicación, y para reclamar recursos.

 Aunque Windows intenta mantener en la memoria tantas aplicaciones suspendidas como sea posible, puede finalizar la tuya si no hay suficientes recursos para conservarla en la memoria. También un usuario podría cerrar tu aplicación de forma explícita. No hay ningún evento especial que indique que un usuario ha cerrado una aplicación.

 En el depurador de Visual Studio, puedes suspender, reanudar y finalizar manualmente las aplicaciones para depurar eventos de ciclo de vida. Para depurar un evento de ciclo de vida:

1. Establezca un punto de interrupción en el controlador del eventos que quiere depurar.

2. Presiona **F5** para iniciar la depuración.

3. En la barra de herramientas **Ubicación de depuración** , elige el evento que desees desencadenar:

     ![Tareas de suspensión, reanudación, terminación y en segundo plano](../debugger/media/dbg_suspendresumebackground.png)

     **Suspender y apagar** cierra la aplicación y finaliza la sesión de depuración.

## <a name="trigger-background-tasks"></a><a name="BKMK_Trigger_background_tasks"></a> Desencadenar tareas en segundo plano
 Aunque no esté en ejecución, cualquier aplicación puede registrar una tarea en segundo plano para responder a determinados eventos del sistema. Las tareas en segundo plano no pueden ejecutar código que actualice directamente la interfaz de usuario. En cambio, muestran información al usuario con las actualizaciones de imágenes y distintivos, y las notificaciones. Para más información, consulte el artículo sobre cómo [admitir la aplicación con tareas en segundo plano](/previous-versions/windows/apps/hh977046(v=win.10)).

 Desde el depurador, puedes desencadenar eventos que inician tareas en segundo plano de tu aplicación.

> [!NOTE]
> El depurador solo puede desencadenar los eventos que no contienen datos, como los que indican un cambio de estado del dispositivo. Tienes que desencadenar manualmente las tareas en segundo plano que requieran datos proporcionados por el usuario o de otro tipo.

 La forma más realista de desencadenar un evento de tarea en segundo plano es hacerlo cuando la aplicación no se está ejecutando. Sin embargo, también es posible desencadenarlo en una sesión de depuración estándar.

### <a name="trigger-a-background-task-event-from-a-standard-debug-session"></a><a name="BKMK_Trigger_a_background_task_event_from_a_standard_debug_session"></a> Desencadenar un evento de tarea en segundo plano desde una sesión de depuración estándar

1. Establece un punto de interrupción en el código de la tarea en segundo plano que quieras depurar.

2. Presiona **F5** para iniciar la depuración.

3. En la lista de eventos de la barra de herramientas **Ubicación de depuración** , elige la tarea en segundo plano que desees iniciar.

     ![Tareas de suspensión, reanudación, terminación y en segundo plano](../debugger/media/dbg_suspendresumebackground.png)

### <a name="trigger-a-background-task-when-the-app-is-not-running"></a><a name="BKMK_Trigger_a_background_task_when_the_app_is_not_running"></a> Desencadenar una tarea en segundo plano cuando la aplicación no se está ejecutando

1. Establece un punto de interrupción en el código de la tarea en segundo plano que quieras depurar.

2. Abre la página de propiedades de depuración del proyecto de inicio. En el Explorador de soluciones, seleccione el proyecto. En el menú **Depurar** , elige **Propiedades**.

     Para los proyectos de C++, expanda **Propiedades de configuración** y elija **Depuración**.

3. Realice una de las siguientes acciones:

    - Para proyectos de Visual C# y Visual Basic, elige **No iniciar, pero depurar mi código al empezar**.

         ![Propiedad de la aplicación de inicio de depuración de C#/VB](../debugger/media/dbg_csvb_dontlaunchapp.png "DBG_CsVb_DontLaunchApp")

    - En los proyectos de C++, elija **No** en la lista **Iniciar aplicación**.

         ![Propiedad de depuración de la aplicación de inicio de C++/VB](../debugger/media/dbg_cppjs_dontlaunchapp.png "DBG_CppJs_DontLaunchApp")

4. Presiona **F5** para poner la aplicación en modo de depuración. Ten en cuenta que la lista **Proceso** de la barra de herramientas **Ubicación de depuración** muestra el nombre del paquete de la aplicación, para indicar que estás en modo de depuración.

     ![Lista de procesos de tareas en segundo plano](../debugger/media/dbg_backgroundtask_processlist.png "DBG_BackgroundTask_ProcessList")

5. En la lista de eventos de la barra de herramientas **Ubicación de depuración** , elige la tarea en segundo plano que desees iniciar.

     ![Suspensión, reanudación, terminación y tareas en segundo plano](../debugger/media/dbg_suspendresumebackground.png "DBG_SuspendResumeBackground")

## <a name="trigger-process-lifetime-management-events-and-background-tasks-from-an-installed-app"></a><a name="BKMK_Trigger_Process_Lifetime_Management_events_and_background_tasks_from_an_installed_app"></a> Desencadenar eventos de la Administración de la duración de los procesos y tareas en segundo plano desde una aplicación instalada
 Use el cuadro de diálogo **Depurar paquete de la aplicación instalada** para cargar una aplicación que ya está instalada en el depurador. Por ejemplo, puede depurar una aplicación instalada desde Microsoft Store o depurar una aplicación si tiene los archivos de origen de la aplicación, pero no tiene un proyecto de Visual Studio para ella. El cuadro de diálogo **Depurar paquete de la aplicación instalada** permite iniciar una aplicación en modo de depuración en la máquina de Visual Studio o en un dispositivo remoto, o bien establecer que la aplicación se ejecute en modo de depuración pero no iniciarla. Para más información, consulte [Depuración de paquete de la aplicación instalada](../debugger/debug-installed-app-package.md).

 Una vez cargada la aplicación en el depurador, puedes usar cualquiera de los procedimientos descritos más arriba.

## <a name="diagnosing-background-task-activation-errors"></a><a name="BKMK_Diagnosing_background_task_activation_errors"></a> Diagnosticar errores de activación de tareas en segundo plano
 Los registros de diagnóstico del Visor de eventos de Windows de la infraestructura de segundo plano contienen información detallada que puedes utilizar para diagnosticar y solucionar problemas de errores de tareas en segundo plano. Para ver el registro:

1. Abra la aplicación Visor de eventos.

2. En el panel **Acciones** , elige **Ver** y asegúrate de que esté activada la casilla **Mostrar registros analíticos y de depuración** .

3. En la barra de herramientas **Visor de eventos (local)** , expande los nodos **Registros de aplicaciones y servicios** > **Microsoft** > **Windows** > **BackgroundTasksInfrastructure**.

4. Elige el registro **Diagnóstico** .

## <a name="see-also"></a>Vea también
- [Prueba de aplicaciones para UWP con Visual Studio](../test/unit-test-your-code.md)
- [Depurar aplicaciones en Visual Studio](debugging-windows-store-and-windows-universal-apps.md)
- [Ciclo de vida de la aplicación](/windows/uwp/launch-resume/app-lifecycle)
- [Launching, resuming, and multitasking](/windows/uwp/launch-resume/index)
