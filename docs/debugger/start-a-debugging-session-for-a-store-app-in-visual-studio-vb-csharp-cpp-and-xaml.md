---
title: Iniciar una sesión de depuración en una aplicación para UWP | Microsoft Docs
ms.custom: seodec18
ms.date: 11/20/2018
ms.topic: how-to
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
ms.openlocfilehash: c4e025603fef11e278aee21b3c44f8d35d7cd34b
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85536557"
---
# <a name="start-a-debugging-session-for-a-uwp-app"></a>Iniciar una sesión de depuración para una aplicación de UWP

En este artículo se describe cómo iniciar una sesión de depuración de Visual Studio en una aplicación para la Plataforma universal de Windows (UWP). Las aplicaciones para UWP se pueden escribir en XAML y C++, XAML y C#/Visual Basic. Para empezar a depurar una aplicación para UWP, configure la sesión de depuración y elija la manera de iniciar la aplicación.

::: moniker range=">=vs-2019"
> [!NOTE]
> A partir de Visual Studio 2019, ya no se admiten las aplicaciones para UWP en HTML y JavaScript.
::: moniker-end
::: moniker range="vs-2017"
En Visual Studio 2017, la mayoría de los comandos y las opciones que se muestran en este artículo también se aplican a las aplicaciones para UWP en HTML y JavaScript. Si los comandos son diferentes entre las aplicaciones administradas y de C++, las aplicaciones de JavaScript suelen ser las mismas que los comandos de las aplicaciones para UWP en C++.
::: moniker-end

## <a name="start-debugging-from-the-visual-studio-toolbar"></a><a name="BKMK_The_easy_way_to_start_debugging"></a>Inicio de la depuración desde la barra de herramientas de Visual Studio

La forma más fácil de configurar e iniciar la depuración es desde la barra de herramientas estándar de Visual Studio.

![Depurar desde la barra de herramientas](../debugger/media/vsrun_select_target_device.png)

1. En el menú desplegable **Configuración** de la barra de herramientas **Estándar**, seleccione **Depurar**.

1. En el menú desplegable **Plataforma**, seleccione la plataforma de destino para la que se va a compilar.

1. En el menú desplegable situado junto a la flecha verde, seleccione el destino de depuración. Puede elegir un equipo local, un dispositivo conectado directamente, un simulador local de Visual Studio, un dispositivo remoto o un emulador.

1. Para iniciar la depuración, seleccione la flecha verde de **Inicio** en la barra de herramientas, o seleccione **Depurar** > **Iniciar depuración** o presione **F5**.

   Visual Studio compila e inicia la aplicación con el depurador asociado.

La depuración continúa hasta que se alcanza un punto de interrupción, se suspende manualmente la ejecución, se produce una excepción no controlada o la aplicación finaliza.

### <a name="deployment-target-options"></a><a name="BKMK_Choose_the_deployment_target"></a> Opciones del destino de la implementación

Puede establecer el destino de depuración en la barra de herramientas de Visual Studio o en la página de propiedades de depuración del proyecto. Seleccione una de las opciones siguientes:

|NOMBRE|Descripción|
|-|-|
|**Equipo local**|Depura la aplicación en la sesión actual en el equipo local.|
|**Simulador**|Depura la aplicación en el simulador de Visual Studio de las aplicaciones para UWP. El simulador es una ventana del escritorio que simula funciones del dispositivo, como gestos táctiles y rotación de dispositivos, que pueden no existir en el equipo local. La opción del simulador solo está disponible si la **Versión mínima de la plataforma de destino** de la aplicación es anterior o igual a la del sistema operativo del equipo local. Para más información, vea [Ejecutar aplicaciones para UWP en el simulador](../debugger/run-windows-store-apps-in-the-simulator.md).|
|**Equipo remoto**|Depura la aplicación en un dispositivo conectado al equipo local a través de una red o un cable Ethernet. Las Herramientas remotas para Visual Studio deben estar instaladas y ejecutándose en el dispositivo remoto. Para más información, vea [Ejecución de aplicaciones para UWP en un equipo remoto](../debugger/run-windows-store-apps-on-a-remote-machine.md).|
|**Dispositivo**|Depura la aplicación en un dispositivo conectado por USB. El dispositivo debe estar desbloqueado por el desarrollador y tener la pantalla desbloqueada.|
|**Emulador de Mobile**|Arranca el emulador especificado en el nombre del emulador, implementa la aplicación e inicia la depuración. Los emuladores solo están disponibles en máquinas con Hyper-V habilitado.|

## <a name="configure-debugging-in-the-project-property-page"></a><a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> Configurar la depuración en la página de propiedades del proyecto

Para configurar opciones de depuración adicionales, use la página de propiedades de depuración del proyecto.

**Para abrir las propiedades de depuración**:

1. En el **Explorador de soluciones**, seleccione el proyecto y, luego, elija el icono de **Propiedades** o haga clic con el botón derecho en el proyecto y seleccione **Propiedades**.

1. En el lado izquierdo del panel **Propiedades**:

   - Para las aplicaciones de C# y Visual Basic, seleccione **Depurar**.

     ![Página de propiedades de depuración de proyectos de C# y Visual Basic](../debugger/media/dbg_csvb_debugpropertypage.png)

   - Para aplicaciones de C++, seleccione **Propiedades de configuración** > **Depuración**.

     ![Página de propiedades de depuración de aplicaciones para UWP en C++](../debugger/media/dbg_cpp_debugpropertypage.png)

### <a name="choose-the-debugger-to-use"></a><a name="BKMK_Choose_the_debugger_to_use"></a> Elegir el depurador utilizado

En las aplicaciones de C# y Visual Basic, Visual Studio depura código administrado de forma predeterminada. Puede optar por depurar otros tipos de código o adicionales. También puede establecer los valores de **Tipo de depurador** para cualquier tarea en segundo plano que forme parte del proyecto.

En aplicaciones de C++, Visual Studio depura el código nativo de forma predeterminada. Puede elegir depurar tipos de código específicos en lugar o además de código nativo.

**Para especificar los tipos de código que se van a depurar**:

- En el caso de las aplicaciones de C# y Visual Basic apps, seleccione uno de los siguientes depuradores en los menús desplegables **Tipo de aplicación** y **Tipo de proceso en segundo plano** en **Tipo de depurador** en la página de propiedades **Depurar**.

- En las aplicaciones de C++, seleccione uno de los siguientes depuradores en el menú desplegable **Tipo de depurador** en la página de propiedades **Depuración**.

|NOMBRE|Descripción|
|-|-|
|**Solo administrado**|Depura el código administrado de la aplicación. Se omiten el código de JavaScript y el de C/C++ nativo.|
|**Solo nativo**|Depura el código C/C++ nativo de la aplicación. Se omiten el código administrado y el de JavaScript.|
|**Mixto (administrado y nativo)**|Depura el código de C/C++ nativo y el código administrado de la aplicación. Se omite el código de JavaScript. En los proyectos de C++, esta opción se denomina **Administrado y nativo**.|
|**Script**|Depura el código JavaScript de la aplicación. Se omiten el código administrado y el nativo.|
|**Código nativo con script**|Depura el código de C/C++ nativo y el código de JavaScript de la aplicación. Se omite el código administrado. Solo está disponible en proyectos de C++ o en tareas en segundo plano.|
|**Solo GPU (C++ AMP)**|Depura el código de C++ nativo que se ejecuta en una unidad de procesamiento gráfico (GPU). Solo está disponible en proyectos de C++.|

### <a name="disable-network-loopbacks-optional"></a><a name="BKMK__Optional__Disable_network_loopbacks"></a> Deshabilitar bucles invertidos de red (opcional)

 Por razones de seguridad, una aplicación para UWP instalada de forma estándar, no puede realizar llamadas de red al dispositivo en el que está instalada. Visual Studio excluye de forma predeterminada las aplicaciones implementadas de esta regla para que pueda probar los procedimientos de comunicación en un solo equipo. Antes de lanzar la aplicación, debe probarla sin la exención.

**Para quitar la exención de bucle invertido de red:**

- Para aplicaciones de C# y Visual Basic, desactive la casilla **Permitir bucle invertido de la red local** en **Opciones de inicio** en la página de propiedades **Depurar**.

- Para aplicaciones de C++, seleccione **No** en el menú desplegable **Permitir bucle invertido de la red local** en la página de propiedades **Depuración**.

### <a name="reinstall-the-app-when-you-start-debugging-optional"></a><a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a> Reinstalar la aplicación al iniciar la depuración (opcional)
 Para diagnosticar problemas de instalación con una aplicación de C# o Visual Basic, seleccione **Desinstalar y reinstalar mi paquete** en la página de propiedades **Depurar**. Esta opción vuelve a crear la instalación original al iniciar la depuración. Esta opción no está disponible para los proyectos de C++.

### <a name="set-authentication-options-for-remote-debugging"></a><a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a> Establecer opciones de autenticación para la depuración remota

De forma predeterminada, debe proporcionar las credenciales de Windows para ejecutar el depurador remoto al seleccionar **Máquina remota** como destino de implementación. Puede cambiar el requisito de autenticación.

El modo de autenticación **Universal (protocolo sin cifrar)** está indicado para los dispositivos IoT, Xbox y HoloLens y para la actualización del creador o equipos Windows 10 con versiones posteriores.

**Para cambiar el modo de autenticación**:

- En el caso de las aplicaciones de C# y Visual Basic, en la página de propiedades **Depurar**, seleccione **Máquina remota** como **Dispositivo de destino**. A continuación, seleccione **Ninguno** o **Universal (protocolo sin cifrar)** para **Modo de autenticación**.

- En el caso de las aplicaciones de C++, seleccione **Máquina remota** en **Depurador para iniciar** en la página de propiedades **Depuración**. A continuación, seleccione **Sin autenticación** o **Universal (protocolo sin cifrar)** para **Tipo de autenticación**.

> [!CAUTION]
> No hay ninguna seguridad de red cuando se ejecuta el depurador remoto en los modos **Ninguno** o **Universal (protocolo sin cifrar)** . Elija estos modos solo en redes de confianza que esté seguro de que no corren riesgos frente a código malintencionado o tráfico hostil.

## <a name="debugging-start-options"></a><a name="BKMK_Start_the_debugging_session"></a> Opciones de inicio de depuración

Al seleccionar **Depurar** > **Iniciar depuración** o presionar **F5**, Visual Studio inicia la aplicación con el depurador adjunto. La ejecución continúa hasta que se alcanza un punto de interrupción, se suspende manualmente la ejecución, se produce una excepción no controlada o la aplicación finaliza.

### <a name="start-debugging-but-delay-app-start"></a><a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a> Iniciar la depuración pero retrasar el inicio de la aplicación

De forma predeterminada, Visual Studio inicia inmediatamente la aplicación cuando se inicia la depuración. Puede establecer que la aplicación se ejecute en modo de depuración, pero iniciarla fuera del depurador. Por ejemplo, puede que quiera depurar el inicio de la aplicación desde el menú **Inicio** de Windows o depurar un proceso en segundo plano en la aplicación. Si elige esta opción, la aplicación se inicia en el depurador al iniciarse.

**Para deshabilitar el inicio automático de la aplicación**:

- Para aplicaciones de C# y Visual Basic, seleccione **No iniciar, pero depurar mi código al empezar** en **Opciones de inicio** en la página de propiedades **Depurar**.

- Para aplicaciones de C++, seleccione **No** en el menú desplegable **Iniciar aplicación** en la página de propiedades **Depuración**.

Para más información sobre la depuración de tareas en segundo plano, vea [Cómo desencadenar eventos de suspensión, reanudación y en segundo plano durante la depuración de aplicaciones para UWP en Visual Studio](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

### <a name="debug-an-installed-or-running-uwp-app"></a><a name="BKMK_Start_an_installed_app_in_the_debugger"></a> Depuración de una aplicación para UWP instalada o en ejecución

Puede usar **Depurar paquete de aplicaciones instalado** para depurar una aplicación para UWP que ya está instalada o en ejecución en un dispositivo local o remoto. Es posible que la aplicación se haya instalado desde Microsoft Store o que no sea un proyecto de Visual Studio. Por ejemplo, la aplicación puede tener un sistema de compilación personalizado que no utilice Visual Studio.

Puede iniciar la aplicación instalada de inmediato, o bien puede configurarla para que se ejecute en el depurador cuando se inicia con otro método. Para más información, vea [Cómo desencadenar eventos de suspensión, reanudación y en segundo plano durante la depuración de aplicaciones para UWP en Visual Studio](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

Para iniciar una aplicación para UWP instalada o en ejecución en el depurador, seleccione **Depurar** > **Otros destinos de depuración** > **Depurar paquete de aplicaciones instalado**. Para más instrucciones, vea [Depuración de paquete de la aplicación instalada](../debugger/debug-installed-app-package.md).

### <a name="attach-the-debugger-to-a-running-windows-8x-app"></a><a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> Asociar el depurador a una aplicación de Windows 8.x en ejecución

Si quieres asociar el depurador a una aplicación de la [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] , debes utilizar el Administrador de paquetes depurables para establecer la aplicación de modo que se ejecute en modo de depuración. El Administrador de paquetes depurables se instala con las Herramientas remotas para Visual Studio.

1. Instale las Herramientas remotas para Visual Studio en el dispositivo donde está instalada la aplicación. Para más información, vea [Instalar las herramientas remotas](../debugger/remote-debugging.md).

1. En la pantalla **Inicio** de Windows, busque e inicie el **Administrador de paquetes depurables**.

   Se abre una ventana de PowerShell configurada correctamente para cmdlet AppxDebug.

1. Especifique el identificador PackageFullName de la aplicación.

   1. Para ver una lista que incluye el identificador PackageFullName de todas las aplicaciones, escriba `Get-AppxPackage` en el símbolo del sistema de PowerShell.

   1. En el símbolo del sistema de PowerShell, escriba `Enable-AppxDebug <PackageFullName>`, donde \<PackageFullName> es el identificador PackageFullName de la aplicación.

1. Seleccione **Depurar** > **Asociar al proceso**.

1. En el cuadro de diálogo **Asociar al proceso**, especifique el dispositivo remoto en el cuadro **Destino de conexión**.

   Puede escribir el nombre del dispositivo, seleccionarlo en la lista desplegable del cuadro **Destino de conexión** o seleccionar **Buscar** para encontrar el dispositivo en el cuadro de diálogo **Conexiones remotas**.

1. Para especificar el tipo de código que desea depurar, junto al cuadro **Asociar a**, elija **Seleccionar**.

1. El cuadro de diálogo **Seleccionar tipo de código**, seleccione:
   - **Determinar automáticamente el tipo de código para depurar** o
   - **Depurar estos tipos de código** y, después, seleccione uno o más tipos de código de la lista.

1. En la lista **Procesos disponibles**, seleccione el proceso de aplicación para depurarlo.

1. Seleccione **Adjuntar**.

 Visual Studio asocia el depurador al proceso. La ejecución continúa hasta que se alcanza un punto de interrupción, se suspende manualmente la ejecución, se produce una excepción no controlada o la aplicación finaliza.

::: moniker range="vs-2017"
> [!NOTE]
> Las aplicaciones de JavaScript se ejecutan en una instancia del proceso *wwahost.exe*. Si se ejecuta más de una aplicación de JavaScript, debe conocer el identificador de proceso numérico (PID) del proceso *wwahost.exe* de la aplicación que se va a adjuntar a él.
>
> La forma más fácil de realizar la asociación a la aplicación de JavaScript es cerrar todas las demás aplicaciones de JavaScript. O bien, puede anotar los PID de ejecutar los procesos *wwahost.exe* en el Administrador de tareas de Windows antes de iniciar la aplicación. Al iniciar la aplicación, el PID de *wwahost.exe* será diferente del que anotó anteriormente.
::: moniker-end

## <a name="see-also"></a>Vea también

- [Depurar aplicaciones en Visual Studio](../debugger/debugging-windows-store-and-windows-universal-apps.md)