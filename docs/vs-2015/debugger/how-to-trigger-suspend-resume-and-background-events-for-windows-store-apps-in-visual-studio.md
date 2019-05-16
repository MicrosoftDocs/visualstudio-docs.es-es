---
title: Cómo desencadenar suspender, reanudar y en segundo plano de los eventos para las aplicaciones de Windows Store
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.error.background_task_activate_failure
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 824ff3ca-fedf-4cf5-b3e2-ac8dc82d40ac
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d341f0550cfa3c978e94152fb792c5b73c68cc74
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65685938"
---
# <a name="how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio"></a>Cómo desencadenar eventos de suspensión, reanudación y en segundo plano para aplicaciones de la Tienda Windows en Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cuando no estás depurando, la **Administración de la duración de los procesos** (PLM) de Windows controla el estado de ejecución de la aplicación, es decir, inicia, suspende, reanuda y finaliza la aplicación en respuesta a las acciones del usuario y al estado del dispositivo. Mientras depuras, Windows deshabilita estos eventos de activación. En este tema se describe cómo activar estos eventos en el depurador.

 También se describe cómo depurar **tareas en segundo plano**. Las tareas en segundo plano te permiten realizar algunas operaciones en un proceso de segundo plano, aunque la aplicación no se esté ejecutando. Puedes utilizar el depurador para poner la aplicación en modo de depuración y, sin iniciar la interfaz de usuario, iniciar y depurar la tarea en segundo plano.

 Para obtener más información sobre la Administración de la duración de los procesos y las tareas en segundo plano, consulta [Launching, resuming, and multitasking](https://msdn.microsoft.com/04307b1b-05af-46a6-b639-3f35e297f71b).

## <a name="BKMK_In_this_topic"></a> En este tema
 [Desencadenar eventos de la Administración de la duración de los procesos](#BKMK_Trigger_Process_Lifecycle_Management_events)

 [Desencadenar tareas en segundo plano](#BKMK_Trigger_background_tasks)

- [Desencadenar un evento de tarea en segundo plano desde una sesión de depuración estándar](#BKMK_Trigger_a_background_task_event_from_a_standard_debug_session)

- [Desencadenar una tarea en segundo plano cuando la aplicación no se está ejecutando](#BKMK_Trigger_a_background_task_when_the_app_is_not_running)

  [Desencadenar eventos de la Administración de la duración de los procesos y tareas en segundo plano desde una aplicación instalada](#BKMK_Trigger_Process_Lifetime_Management_events_and_background_tasks_from_an_installed_app)

  [Diagnosticar errores de activación de tareas en segundo plano](#BKMK_Diagnosing_background_task_activation_errors)

## <a name="BKMK_Trigger_Process_Lifecycle_Management_events"></a> Desencadenar eventos de la Administración de la duración de los procesos
 Windows puede suspender la aplicación cuando el usuario cambia a otra aplicación o cuando Windows entra en estado de baja energía. Puedes responder al evento `Suspending` para guardar los datos pertinentes de la aplicación y del usuario en el almacenamiento persistente, y para liberar recursos. Cuando una aplicación se reanuda del estado **suspendido** , entra en el estado de **ejecución** y sigue desde el punto donde se suspendió. Puedes responder al evento `Resuming` para restaurar o actualizar el estado de la aplicación, y para reclamar recursos.

 Aunque Windows intenta mantener en la memoria tantas aplicaciones suspendidas como sea posible, puede finalizar la tuya si no hay suficientes recursos para conservarla en la memoria. También un usuario podría cerrar tu aplicación de forma explícita. No hay ningún evento especial que indique que un usuario ha cerrado una aplicación.

 En el depurador de Visual Studio, puedes suspender, reanudar y finalizar manualmente las aplicaciones para depurar eventos de ciclo de vida. Para depurar un evento de ciclo de vida:

1. Establece un punto de interrupción en el controlador del eventos que quieres depurar.

2. Presiona **F5** para iniciar la depuración.

3. En la barra de herramientas **Ubicación de depuración** , elige el evento que desees desencadenar:

     ![Suspender, reanudar, terminar y tareas en segundo plano](../debugger/media/dbg-suspendresumebackground.png "DBG_SuspendResumeBackground")

     Observa que **Suspender y apagar** cierra la aplicación y finaliza la sesión de depuración.

## <a name="BKMK_Trigger_background_tasks"></a> Desencadenar tareas en segundo plano
 Aunque no esté en ejecución, cualquier aplicación puede registrar una tarea en segundo plano para responder a determinados eventos del sistema. Las tareas en segundo plano no pueden ejecutar código que actualice directamente la interfaz de usuario. En cambio, muestran información al usuario con las actualizaciones de imágenes y distintivos, y las notificaciones. Para obtener más información, vea [Supporting your app with background tasks](https://msdn.microsoft.com/4c7bb148-eb1f-4640-865e-41f627a46e8e)

 Desde el depurador, puedes desencadenar eventos que inician tareas en segundo plano de tu aplicación.

> [!NOTE]
> El depurador solo puede desencadenar los eventos que no contienen datos, como los que indican un cambio de estado del dispositivo. Tienes que desencadenar manualmente las tareas en segundo plano que requieran datos proporcionados por el usuario o de otro tipo.

 La forma más realista de desencadenar un evento de tarea en segundo plano es hacerlo cuando la aplicación no se está ejecutando. Sin embargo, también es posible desencadenarlo en una sesión de depuración estándar.

### <a name="BKMK_Trigger_a_background_task_event_from_a_standard_debug_session"></a> Desencadenar un evento de tarea en segundo plano desde una sesión de depuración estándar

1. Establece un punto de interrupción en el código de la tarea en segundo plano que quieras depurar.

2. Presiona **F5** para iniciar la depuración.

3. En la lista de eventos de la barra de herramientas **Ubicación de depuración** , elige la tarea en segundo plano que desees iniciar.

     ![Suspender, reanudar, terminar y tareas en segundo plano](../debugger/media/dbg-suspendresumebackground.png "DBG_SuspendResumeBackground")

### <a name="BKMK_Trigger_a_background_task_when_the_app_is_not_running"></a> Desencadenar una tarea en segundo plano cuando la aplicación no se está ejecutando

1. Establece un punto de interrupción en el código de la tarea en segundo plano que quieras depurar.

2. Abre la página de propiedades de depuración del proyecto de inicio. En el Explorador de soluciones, seleccione el proyecto. En el menú **Depurar** , elige **Propiedades**.

     Para los proyectos de C++, es posible que tengas que expandir **Propiedades de configuración** y elegir **Depuración**.

3. Realice una de las siguientes acciones:

    - Para proyectos de Visual C# y Visual Basic, elige **No iniciar, pero depurar mi código al empezar**.

         ![C&#35;&#47;propiedad de aplicación de inicio de depuración VB](../debugger/media/dbg-csvb-dontlaunchapp.png "DBG_CsVb_DontLaunchApp")

    - Para los proyectos de JavaScript y Visual C++, elige **No** en la lista **Iniciar aplicación** .

         ![C&#43;&#43;&#47;propiedad de depuración de aplicaciones de VB iniciar](../debugger/media/dbg-cppjs-dontlaunchapp.png "DBG_CppJs_DontLaunchApp")

4. Presiona **F5** para poner la aplicación en modo de depuración. Ten en cuenta que la lista **Proceso** de la barra de herramientas **Ubicación de depuración** muestra el nombre del paquete de la aplicación, para indicar que estás en modo de depuración.

     ![Lista de procesos de tareas en segundo plano](../debugger/media/dbg-backgroundtask-processlist.png "DBG_BackgroundTask_ProcessList")

5. En la lista de eventos de la barra de herramientas **Ubicación de depuración** , elige la tarea en segundo plano que desees iniciar.

     ![Suspender, reanudar, terminar y tareas en segundo plano](../debugger/media/dbg-suspendresumebackground.png "DBG_SuspendResumeBackground")

## <a name="BKMK_Trigger_Process_Lifetime_Management_events_and_background_tasks_from_an_installed_app"></a> Desencadenar eventos de la Administración de la duración de los procesos y tareas en segundo plano desde una aplicación instalada
 Utiliza el cuadro de diálogo Depurar aplicación instalada para cargar una aplicación que ya esté instalada en el depurador. Por ejemplo, puedes depurar una aplicación instalada desde la Tienda Windows o depurar una aplicación si tienes los archivos de origen de la aplicación pero no tienes un proyecto de Visual Studio para ella. El cuadro de diálogo Depurar aplicación instalada te permite iniciar una aplicación en modo de depuración en el equipo de Visual Studio o en un dispositivo remoto, o establecer que la aplicación se ejecute en modo de depuración pero no iniciarla. Consulta la sección **Iniciar una aplicación instalada en el depurador** de las versiones de [JavaScript](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md#BKMK_Start_an_installed_app_in_the_debugger) o [Visual C++, Visual C# y Visual Basic](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md#BKMK_Start_an_installed_app_in_the_debugger) de **Iniciar una sesión de depuración** para obtener más información.

 Una vez cargada la aplicación en el depurador, puedes usar cualquiera de los procedimientos descritos más arriba.

## <a name="BKMK_Diagnosing_background_task_activation_errors"></a> Diagnosticar errores de activación de tareas en segundo plano
 Los registros de diagnóstico del Visor de eventos de Windows de la infraestructura de segundo plano contienen información detallada que puedes utilizar para diagnosticar y solucionar problemas de errores de tareas en segundo plano. Para ver el registro:

1. Abra la aplicación Visor de eventos.

2. En el panel **Acciones** , elige **Ver** y asegúrate de que esté activada la casilla **Mostrar registros analíticos y de depuración** .

3. En la barra de herramientas **Visor de eventos (local)** , expande los nodos **Registros de aplicaciones y servicios** / **Microsoft** / **Windows** / **BackgroundTasksInfrastructure**.

4. Elige el registro **Diagnóstico** .

## <a name="see-also"></a>Vea también
 [Probar aplicaciones de Store con Visual Studio](../test/testing-store-apps-with-visual-studio.md) [depurar aplicaciones en Visual Studio](../debugger/debug-store-apps-in-visual-studio.md) [ciclo de vida de aplicación](https://msdn.microsoft.com/53cdc987-c547-49d1-a5a4-fd3f96b2259d) [Launching, resuming, procesos y tareas](https://msdn.microsoft.com/04307b1b-05af-46a6-b639-3f35e297f71b)
