---
title: Iniciar una sesión de depuración para una aplicación para UWP | Microsoft Docs
ms.custom: seodec18
ms.date: 11/20/2018
ms.topic: conceptual
f1_keywords:
- VC.Project.IVCAppHostRemoteDebugPageObject.MachineName
- VC.Project.IVCAppHostRemoteDebugPageObject.BreakpointBehavior
- VC.Project.IVCAppHostLocalDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostTetheredDebugPageObject.DebuggerType
- VC.Project.IVCAppHostLocalDebugPageObject.BreakpointBehavior
- VC.Project.IVCAppHostRemoteDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostRemoteDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostLocalDebugPageObject.DebuggerType
- VC.Project.IVCAppHostSimulatorDebugPageObject.DebuggerType
- ImmersiveProjects.Properties.Debug
- VC.Project.IVCAppHostTetheredDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostSimulatorDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostSimulatorDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostLocalDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostLocalDebugPageObject.AllowLocalNetworkLoopback
- AppPackage.Properties.Debug
- VC.Project.IVCAppHostRemoteDebugPageObject.Authentication
- VC.Project.IVCAppHostRemoteDebugPageObject.DebuggerType
- VC.Project.IVCAppHostSimulatorDebugPageObject.BreakpointBehavior
- vs.debug.installedapppackagelauncher
- vs.debug.error.wwahost_scriptdebuggingdisabled
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
ms.openlocfilehash: c4504dda362c8a50f33168a12839e894a14316d7
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72436005"
---
# <a name="start-a-debugging-session-for-a-uwp-app"></a>Iniciar una sesión de depuración para una aplicación de UWP

En este artículo se describe cómo iniciar una sesión de depuración de Visual Studio para una aplicación Plataforma universal de Windows (UWP). Las aplicaciones UWP se pueden escribir en XAML C++y, XAML C#y/Visual Basic. Para iniciar la depuración de una aplicación para UWP, configure la sesión de depuración y elija la manera de iniciar la aplicación.

::: moniker range=">=vs-2019"
> [!NOTE]
> A partir de Visual Studio 2019, ya no se admiten las aplicaciones UWP para HTML y JavaScript.
::: moniker-end
::: moniker range="vs-2017"
En Visual Studio 2017, la mayoría de los comandos y las opciones que se muestran en este artículo también se aplican a las aplicaciones para UWP para HTML y JavaScript. Si los comandos son diferentes entre las C++ aplicaciones administradas y, las aplicaciones de JavaScript suelen ser C++ las mismas que los comandos de las aplicaciones para UWP.
::: moniker-end

## <a name="BKMK_The_easy_way_to_start_debugging"></a>Iniciar la depuración desde la barra de herramientas de Visual Studio

La forma más fácil de configurar e iniciar la depuración es desde la barra de herramientas estándar de Visual Studio.

![Depurar desde la barra de herramientas](../debugger/media/vsrun_select_target_device.png)

1. En el menú desplegable **configuración** de la barra de herramientas **estándar** , seleccione **depurar**.

1. En la lista desplegable **plataforma** , seleccione la plataforma de destino para la que se va a compilar.

1. En la lista desplegable situada junto a la flecha verde, seleccione el destino de depuración. Puede elegir un equipo local, un dispositivo conectado directamente, un simulador local de Visual Studio, un dispositivo remoto o un emulador.

1. Para iniciar la depuración, seleccione la flecha de **Inicio** verde en la barra de herramientas o seleccione **depurar**  > **iniciar depuración**o presione **F5**.

   Visual Studio compila e inicia la aplicación con el depurador asociado.

La depuración continúa hasta que se alcanza un punto de interrupción, se suspende manualmente la ejecución, se produce una excepción no controlada o la aplicación finaliza.

### <a name="BKMK_Choose_the_deployment_target"></a>Opciones de destino de implementación

Puede establecer el destino de depuración en la barra de herramientas de Visual Studio o en la página de propiedades depuración del proyecto. Seleccione una de las opciones siguientes:

|||
|-|-|
|**Equipo local**|Depura la aplicación en la sesión actual en el equipo local.|
|**Simulador**|Depure la aplicación en el simulador de Visual Studio para aplicaciones para UWP. El simulador es una ventana del escritorio que simula funciones de dispositivo, como gestos táctiles y rotación de dispositivos, que puede que no existan en el equipo local. La opción del simulador solo está disponible si la **versión mínima** de la plataforma de destino de la aplicación es menor o igual que el sistema operativo del equipo local. Para obtener más información, vea [ejecutar aplicaciones para UWP en el simulador](../debugger/run-windows-store-apps-in-the-simulator.md).|
|**Equipo remoto**|Depure la aplicación en un dispositivo conectado al equipo local a través de una red o un cable Ethernet. El Herramientas remotas para Visual Studio debe estar instalado y en ejecución en el dispositivo remoto. Para obtener más información, consulte [ejecución de aplicaciones para UWP en un equipo remoto](../debugger/run-windows-store-apps-on-a-remote-machine.md).|
|**Dispositivo**|Depure la aplicación en un dispositivo conectado USB. El dispositivo debe estar desbloqueado por el desarrollador y tener la pantalla desbloqueada.|
|**Emulador móvil**|Arranque el emulador especificado en el nombre del emulador, implemente la aplicación e inicie la depuración. Los emuladores solo están disponibles en máquinas con Hyper-V habilitadas.|

## <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a>Configurar la depuración en la página de propiedades del proyecto

Para configurar opciones de depuración adicionales, use la página Propiedades de depuración del proyecto.

**Para abrir las propiedades de depuración:**

1. En **Explorador de soluciones**, seleccione el proyecto y, a continuación, seleccione el icono **propiedades** , o haga clic con el botón derecho en el proyecto y seleccione **propiedades**.

1. En el lado izquierdo del panel de **propiedades** :

   - Para C# las aplicaciones de y Visual Basic, seleccione **depurar**.

     ![C#y Visual Basic página de propiedades Depurar proyecto](../debugger/media/dbg_csvb_debugpropertypage.png)

   - En C++ el caso de **las** aplicaciones, seleccione Propiedades de configuración  > **depuración**.

     ![C++Página de propiedades de depuración de aplicaciones para UWP](../debugger/media/dbg_cpp_debugpropertypage.png)

### <a name="BKMK_Choose_the_debugger_to_use"></a> Elegir el depurador utilizado

En C# el caso de las aplicaciones y Visual Basic, Visual Studio depura el código administrado de forma predeterminada. Puede optar por depurar otros tipos de código o adicionales. También puede establecer los valores del **tipo de depurador** para cualquier tarea en segundo plano que forme parte del proyecto.

En C++ las aplicaciones de, Visual Studio depura el código nativo de forma predeterminada. Puede elegir depurar tipos de código específicos en lugar de código nativo, o además de él.

**Para especificar los tipos de código que se van a depurar:**

- En C# el caso de las aplicaciones de y Visual Basic, seleccione uno de los siguientes depuradores de las listas desplegables tipo de **aplicación** y **tipo de proceso en segundo plano** en **tipo de depurador** en la página de propiedades **depurar** .

- En C++ el caso de las aplicaciones, seleccione uno de los siguientes depuradores en la lista desplegable **tipo de depurador** de la página de propiedades **depuración** .

|||
|-|-|
|**Solo administrado**|Depura el código administrado de la aplicación. Se omiten el código de JavaScript y el de C/C++ nativo.|
|**Solo nativo**|Depura el código C/C++ nativo de la aplicación. Se omiten el código administrado y el de JavaScript.|
|**Mixto (administrado y nativo)**|Depura el código de C/C++ nativo y el código administrado de la aplicación. Se omite el código de JavaScript. En C++ los proyectos de, esta opción se denomina **Administración y nativa**.|
|**Script**|Depura el código JavaScript de la aplicación. Se omiten el código administrado y el nativo.|
|**Código nativo con script**|Depure código CC++ /Code nativo y código JavaScript en la aplicación. Se omite el código administrado. Disponible solo C++ en proyectos o tareas en segundo plano.|
|**Solo GPU (C++ AMP)**|Depura el código de C++ nativo que se ejecuta en una unidad de procesamiento gráfico (GPU). Solo está C++ disponible en proyectos de.|

### <a name="BKMK__Optional__Disable_network_loopbacks"></a>Deshabilitar bucles invertidos de red (opcional)

 Por seguridad, una aplicación para UWP que se instala de forma estándar no puede realizar llamadas de red al dispositivo en el que está instalado. Visual Studio excluye de forma predeterminada las aplicaciones implementadas de esta regla para que pueda probar los procedimientos de comunicación en un solo equipo. Antes de publicar la aplicación, debe probar la aplicación sin la exención.

**Para quitar la exención de bucle invertido de red:**

- Para C# las aplicaciones y Visual Basic, desactive la casilla **permitir bucle invertido de la red local** en **Opciones de inicio** en la página de propiedades **depurar** .

- En C++ el caso de las aplicaciones, seleccione **no** en la lista desplegable **permitir bucle invertido de red local** en la página de propiedades **depuración** .

### <a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a>Reinstalar la aplicación al iniciar la depuración (opcional)
 Para diagnosticar problemas de instalación con C# una aplicación de o Visual Basic, seleccione **desinstalar y reinstalar mi paquete** en la página de propiedades **depurar** . Esta opción vuelve a crear la instalación original al iniciar la depuración. Esta opción no está disponible C++ para los proyectos de.

### <a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a>Establecer opciones de autenticación para la depuración remota

De forma predeterminada, debe proporcionar las credenciales de Windows para ejecutar el depurador remoto al seleccionar **equipo remoto** como destino de implementación. Puede cambiar el requisito de autenticación.

El modo de autenticación **universal (protocolo sin cifrar)** es para dispositivos IOT, Xbox y HoloLens, y la actualización del creador o de equipos con Windows 10 posteriores.

**Para cambiar el método de autenticación:**

- Para C# las aplicaciones de y Visual Basic, en la página de propiedades **depurar** , seleccione **equipo remoto** como **dispositivo de destino**. A continuación, seleccione **ninguno** o **universal (protocolo sin cifrar)** para el **modo de autenticación**.

- En C++ el caso de las aplicaciones, seleccione **equipo remoto** en **depurador para iniciar** en la página de propiedades **depuración** . A continuación, seleccione **sin autenticación** o **universal (protocolo sin cifrar)** para el **tipo de autenticación**.

> [!CAUTION]
> No hay ninguna seguridad de red cuando se ejecuta el depurador remoto en los modos **ninguno** o **universal (protocolo sin cifrar)** . Elija estos modos solo en redes de confianza que esté seguro de que no corren riesgo de ser un código malintencionado o un tráfico hostil.

## <a name="BKMK_Start_the_debugging_session"></a>Opciones de inicio de depuración

Al seleccionar **Depurar**  > **iniciar depuración** o presionar **F5**, Visual Studio inicia la aplicación con el depurador adjunto. La ejecución continúa hasta que se alcanza un punto de interrupción, se suspende manualmente la ejecución, se produce una excepción no controlada o la aplicación finaliza.

### <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a>Iniciar la depuración pero retrasar el inicio de la aplicación

De forma predeterminada, Visual Studio inicia la aplicación inmediatamente al iniciar la depuración. También puede establecer que la aplicación se ejecute en modo de depuración, pero iniciar la aplicación fuera del depurador. Por ejemplo, puede que quiera depurar el inicio de la aplicación desde el menú **Inicio** de Windows o depurar un proceso en segundo plano en la aplicación. Si elige esta opción, la aplicación se inicia en el depurador al iniciarse.

**Para deshabilitar el inicio automático de la aplicación:**

- Para C# las aplicaciones de y Visual Basic, seleccione **no iniciar, pero depurar mi código cuando se inicie** en **Opciones de inicio** en la página de propiedades **depurar** .

- En C++ el caso de las aplicaciones, seleccione **no** en la lista desplegable **Iniciar aplicación** de la página de propiedades **depuración** .

Para obtener más información sobre la depuración de tareas en segundo plano, vea [desencadenar eventos de suspensión, reanudación y en segundo plano para aplicaciones UWP](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

### <a name="BKMK_Start_an_installed_app_in_the_debugger"></a>Depuración de una aplicación para UWP instalada o en ejecución

Puede usar **depurar paquete de aplicaciones instalado** para depurar una aplicación para UWP que ya está instalada o en ejecución en un dispositivo local o remoto. Es posible que la aplicación se haya instalado desde el Microsoft Store, o que no sea un proyecto de Visual Studio. Por ejemplo, la aplicación podría tener un sistema de compilación personalizado que no use Visual Studio.

Puede iniciar la aplicación instalada de inmediato, o bien puede configurarla para que se ejecute en el depurador cuando se inicia con otro método. Para obtener más información, vea [desencadenar eventos de suspensión, reanudación y en segundo plano para aplicaciones de UWP](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

Para iniciar una aplicación de UWP instalada o en ejecución en el depurador, seleccione **Depurar**  > **otros destinos de depuración**  > **depurar paquete de aplicaciones instalado**. Para obtener más instrucciones, consulte [depuración de un paquete de aplicaciones instalado](../debugger/debug-installed-app-package.md).

### <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a>Asociar el depurador a una aplicación de Windows 8. x en ejecución

Si quieres asociar el depurador a una aplicación de la [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] , debes utilizar el Administrador de paquetes depurables para establecer la aplicación de modo que se ejecute en modo de depuración. El administrador de paquetes depurables se instala con el Herramientas remotas para Visual Studio.

1. Instale el Herramientas remotas para Visual Studio en el dispositivo donde está instalada la aplicación. Para obtener más información, vea [instalar las herramientas remotas](../debugger/remote-debugging.md).

1. En la pantalla **Inicio** de Windows, busque e inicie el **Administrador de paquetes depurables**.

   Se abre una ventana de PowerShell configurada correctamente para cmdlet AppxDebug.

1. Especifique el identificador PackageFullName de la aplicación.

   1. Para ver una lista que incluya el PackageFullName de todas las aplicaciones, escriba `Get-AppxPackage` en el símbolo del sistema de PowerShell.

   1. En el símbolo del sistema de PowerShell, escriba `Enable-AppxDebug <PackageFullName>`, donde \<PackageFullName > es el identificador PackageFullName de la aplicación.

1. Seleccione **Depurar** > **Asociar al proceso**.

1. En el cuadro de diálogo **asociar al proceso** , especifique el dispositivo remoto en el cuadro destino de la **conexión** .

   Puede escribir el nombre del dispositivo, seleccionarlo en la lista desplegable del cuadro destino de la **conexión** o seleccionar **Buscar** para buscar el dispositivo en el cuadro de diálogo **conexiones remotas** .

1. Para especificar el tipo de código que desea depurar, junto al cuadro **asociar a** , seleccione **seleccionar**.

1. En el cuadro de diálogo **Seleccionar tipo de código** , seleccione:
   - **Determinar automáticamente el tipo de código que se va a depurar**o
   - **Depure estos tipos de código**y, a continuación, seleccione uno o más tipos de código de la lista.

1. En la lista **procesos disponibles** , seleccione el proceso de la aplicación que se va a depurar.

1. Seleccione **adjuntar**.

 Visual Studio asocia el depurador al proceso. La ejecución continúa hasta que se alcanza un punto de interrupción, se suspende manualmente la ejecución, se produce una excepción no controlada o la aplicación finaliza.

::: moniker range="vs-2017"
> [!NOTE]
> Las aplicaciones de JavaScript se ejecutan en una instancia del proceso *wwahost.exe*. Si se está ejecutando más de una aplicación de JavaScript, deberá conocer el identificador de proceso numérico (PID) del proceso *wwahost. exe* de la aplicación para adjuntarlo.
>
> La forma más fácil de asociar a la aplicación de JavaScript es cerrar todas las demás aplicaciones de JavaScript. O bien, puede anotar los PID de la ejecución de procesos de *wwahost. exe* en el administrador de tareas de Windows antes de iniciar la aplicación. Al iniciar la aplicación, el PID de *wwahost. exe* será el que sea distinto de los que anotó anteriormente.
::: moniker-end

## <a name="see-also"></a>Vea también

- [Depurar aplicaciones en Visual Studio](../debugger/debugging-windows-store-and-windows-universal-apps.md)