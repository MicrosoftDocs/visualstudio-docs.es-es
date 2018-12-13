---
title: Iniciar una sesión de depuración para una aplicación para UWP | Microsoft Docs
ms.custom: seodec18
ms.date: 11/20/2018
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 181dec6bfa6ebe96528c39b74d68375b8eb7fcb8
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062414"
---
# <a name="start-a-debugging-session-for-a-uwp-app"></a>Iniciar una sesión de depuración para una aplicación de UWP
  
En este artículo se describe cómo iniciar una sesión de depuración de Visual Studio para una aplicación de plataforma Universal de Windows (UWP). Se pueden escribir aplicaciones para UWP en XAML y C++, XAML y C#o, o HTML y JavaScript. Para iniciar la depuración de una aplicación para UWP, configure la sesión de depuración y elija la manera de iniciar la aplicación.  
  
##  <a name="BKMK_The_easy_way_to_start_debugging"></a>Iniciar la depuración desde la barra de herramientas de Visual Studio 
  
Es la manera más fácil de configurar e iniciar la depuración desde la barra de herramientas estándar de Visual Studio. 

![Depurar desde la barra de herramientas](../debugger/media/vsrun_select_target_device.png)  
  
1. Desde el **configuración** lista desplegable en el **estándar** barra de herramientas, seleccione **depurar**.  
  
1. Desde el **plataforma** lista desplegable, seleccione la plataforma de destino para crear aplicaciones para. 
   
1. En la lista desplegable situada junto a la flecha verde, seleccione el destino de depuración. Puede elegir un equipo local, los dispositivos conectados directamente, local simulador de Visual Studio, dispositivo remoto o emulador. 
   
1. Para iniciar la depuración, seleccione el color verde **iniciar** flecha en la barra de herramientas, o bien seleccione **depurar** > **Iniciar depuración**, o bien presione **F5**. 
   
   Visual Studio compila e inicia la aplicación con el depurador asociado. 

Depuración continúa hasta que se alcanza un punto de interrupción, se suspende manualmente la ejecución, se produce una excepción no controlada, o la aplicación finaliza.  
  
###  <a name="BKMK_Choose_the_deployment_target"></a> Opciones de implementación de destino 
  
Puede establecer el destino de depuración en la barra de herramientas de Visual Studio o el proyecto de depuración de página de propiedades. Seleccione una de las opciones siguientes:

|||  
|-|-|  
|**Equipo local**|Depura la aplicación en la sesión actual en el equipo local.|  
|**Simulador**|Depurar la aplicación en el simulador de Visual Studio para aplicaciones UWP. El simulador es una ventana del escritorio que simula las funciones de dispositivo, como la interacción de gestos y rotación de dispositivos, que no exista en el equipo local. La opción de simulador está disponible solo si la aplicación **mínima de la plataforma de destino. Versión** es menor o igual que el sistema operativo en el equipo local. Para obtener más información, consulte [ejecutar aplicaciones para UWP en el simulador](../debugger/run-windows-store-apps-in-the-simulator.md).|  
|**Equipo remoto**|Depurar la aplicación en un dispositivo conectado al equipo local a través de una red o un cable Ethernet. Herramientas remotas para Visual Studio debe estar instalado y ejecutándose en el dispositivo remoto. Para obtener más información, consulte [ejecutar aplicaciones para UWP en un equipo remoto](../debugger/run-windows-store-apps-on-a-remote-machine.md).|  
|**Dispositivo**|Depurar la aplicación en un dispositivo USB conectado. El dispositivo debe estar desbloqueada de desarrollador y tiene la pantalla desbloqueada.|  
|**Emulador de dispositivos móvil**|Inicie el emulador especificado en el nombre del emulador, implemente la aplicación e iniciar la depuración. Los emuladores solo están disponibles en las máquinas de Hyper-V habilitado.|  

##  <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> Configurar la depuración en la página de propiedades del proyecto 

Para configurar otras opciones de depuración, use la página de propiedades de depuración del proyecto. 

**Para abrir las propiedades de depuración:**

1. En **el Explorador de soluciones**, seleccione el proyecto y, a continuación, seleccione el **propiedades** icono, o haga clic en el proyecto y seleccione **propiedades**.  
   
1. En el lado izquierdo de la **propiedades** panel:
   
   - Para C# y aplicaciones de Visual Basic, seleccionadas **depurar**.  
     
     ![C#y la página de propiedades de depuración de proyecto de Visual Basic](../debugger/media/dbg_csvb_debugpropertypage.png)  
   
   - Para las aplicaciones de C++ y JavaScript, seleccione **propiedades de configuración** > **depuración**.  
     
     ![Página de propiedades de depuración de la aplicación de UWP de C++](../debugger/media/dbg_cpp_debugpropertypage.png)  

###  <a name="BKMK_Choose_the_debugger_to_use"></a> Elegir el depurador utilizado  

Para C# y las aplicaciones de Visual Basic, Visual Studio depura código administrado de forma predeterminada. Puede depurar código adicionales u otros tipos. También puede establecer **el tipo de depurador** valores para las tareas en segundo plano que forman parte del proyecto.

En las aplicaciones de C++, Visual Studio depura código nativo de forma predeterminada. En las aplicaciones de JavaScript, Visual Studio depura el script de forma predeterminada. Puede depurar determinados tipos de código en lugar de, o además de código nativo. 

**Para especificar los tipos de código para depurar:**

- Para C# y las aplicaciones de Visual Basic, seleccione uno de los depuradores siguientes en el **tipo de aplicación** y **tipo de proceso en segundo plano** listas desplegables en **el tipo de depurador** en el **depurar** página de propiedades.  
  
- Para C++ / c++ / aplicaciones de JavaScript, seleccione uno de los depuradores siguientes desde el **tipo de depurador** lista desplegable en el **depuración** página de propiedades.

|||  
|-|-|  
|**Solo administrado**|Depura el código administrado de la aplicación. Se omiten el código de JavaScript y el de C/C++ nativo.|  
|**Solo nativo**|Depura el código C/C++ nativo de la aplicación. Se omiten el código administrado y el de JavaScript.|  
|**Mixto (administrado y nativo)**|Depura el código de C/C++ nativo y el código administrado de la aplicación. Se omite el código de JavaScript. En los proyectos de C++, esta opción se denomina **administrado y nativo**.|  
|**Script**|Depura el código JavaScript de la aplicación. Se omiten el código administrado y el nativo.|  
|**Código nativo con script**|Depurar código de C/C ++ nativo y código de JavaScript de la aplicación. Se omite el código administrado. Está disponible en los proyectos de C++ o únicamente en tareas en segundo plano.|  
|**Solo GPU (C++ AMP)**|Depura el código de C++ nativo que se ejecuta en una unidad de procesamiento gráfico (GPU). Está disponible en los proyectos de C++.|  

  
###  <a name="BKMK__Optional__Disable_network_loopbacks"></a> Deshabilitar bucles invertidos de red (opcional) 
  
 Para la seguridad, una aplicación para UWP que se instala en la manera estándar no puede realizar en el dispositivo en que está instalado las llamadas de red. Exime Visual Studio implementa las aplicaciones de esta regla de forma predeterminada, para que pueda probar los procedimientos de comunicación en una sola máquina. Antes de publicar la aplicación, debe probarla sin la exención.  
  
**Para quitar la exención de bucle invertido de red:**  
  
-   Para C# y anule la selección de las aplicaciones de Visual Basic, el **permitir bucle invertido de red local** casilla de verificación bajo **opciones de inicio** en el **depurar** página de propiedades.  
  
-   Para las aplicaciones de Visual C++ y JavaScript, seleccione **No** desde el **permitir bucle invertido de red Local** lista desplegable en el **depuración** página de propiedades.  
  
###  <a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a> Vuelva a instalar la aplicación al iniciar la depuración (opcional) 
 Para diagnosticar problemas de instalación con un C# o aplicación de Visual Basic, seleccione **desinstalar y reinstalar mi paquete** en el **depurar** página de propiedades. Esta opción vuelve a crear la instalación original al iniciar la depuración. Esta opción no está disponible para los proyectos de C++ y JavaScript.  
  
###  <a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a> Establecer las opciones de autenticación para la depuración remota  
  
De forma predeterminada, debe proporcionar las credenciales de Windows para ejecutar el depurador remoto cuando se selecciona **máquina remota** como el destino de implementación. Puede cambiar el requisito de autenticación. 

El **Universal (protocolo sin cifrar)** es el modo de autenticación para dispositivos de IoT, Xbox y HoloLens y actualización o equipos posteriores de Windows 10 del creador.  

**Para cambiar el método de autenticación:**  

- Para C# y las aplicaciones de Visual Basic, en el **depurar** página de propiedades, seleccione **máquina remota** como el **dispositivo de destino**. A continuación, seleccione **ninguno** o **Universal (protocolo sin cifrar)** para **modo de autenticación**. 
  
- Para las aplicaciones de C++ y JavaScript, seleccione **máquina remota** en **depurador para iniciar** en el **depuración** página de propiedades. A continuación, seleccione **sin autenticación** o **Universal (protocolo sin cifrar)** para **tipo de autenticación**. 
  
> [!CAUTION]
> No hay ninguna seguridad de red al ejecutar el depurador remoto en **ninguno** o **Universal (protocolo sin cifrar)** modos. Elija estos modos solo en redes de confianza que se está seguro de que no son expuestos a código malintencionado o tráfico hostil.  
  
##  <a name="BKMK_Start_the_debugging_session"></a> Opciones de inicio de depuración  
  
Al seleccionar **depurar** > **Iniciar depuración** o presione **F5**, Visual Studio inicia la aplicación con el depurador adjunto. La ejecución continúa hasta que se alcanza un punto de interrupción, se suspende manualmente la ejecución, se produce una excepción no controlada o la aplicación finaliza.  
  
###  <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a> Iniciar la depuración pero retrasar el inicio de aplicación  

De forma predeterminada, Visual Studio inicia la aplicación inmediatamente al iniciar la depuración. También puede establecer la aplicación se ejecute en modo de depuración, pero iniciar la aplicación fuera del depurador. Por ejemplo, desea depurar el inicio de la aplicación de la Windows **iniciar** menú o depurar un proceso en segundo plano en la aplicación. Si elige esta opción, se inicia la aplicación en el depurador en el inicio. 

**Para deshabilitar el inicio de la aplicación automática:**  
  
- Para C# y aplicaciones de Visual Basic, seleccionadas **no iniciar, pero depurar mi código al empezar** en **opciones de inicio** en el **depurar** página de propiedades.  
   
- Para las aplicaciones de C++ y JavaScript, seleccione **No** desde el **Iniciar aplicación** lista desplegable en el **depuración** página de propiedades.  
  
Para obtener más información sobre la depuración de tareas en segundo plano, vea [desencadenador suspender, reanudar y en segundo plano de los eventos de aplicaciones para UWP](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).  
  
###  <a name="BKMK_Start_an_installed_app_in_the_debugger"></a> Depurar una aplicación UWP instalada o en ejecución 

Puede usar **depurar paquete de aplicaciones instalado** para depurar una aplicación para UWP que ya está instalado o está ejecutando en un dispositivo local o remoto. Pudo haber instalado la aplicación desde la Microsoft Store, o puede que no sea un proyecto de Visual Studio. Por ejemplo, la aplicación podría tener un sistema de compilación personalizada que no usa Visual Studio.  
  
Puede iniciar inmediatamente la aplicación instalada, o puede establecer que se ejecute en el depurador cuando se inicia con otro método. Para obtener más información, consulte [desencadenador suspender, reanudar y en segundo plano de los eventos para aplicaciones UWP)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).  
  
Para iniciar una aplicación para UWP instalada ni se ejecuta en el depurador, seleccione **depurar** > **otros destinos de depuración** > **depurar paquete de aplicaciones instalado**. Para obtener más instrucciones, consulte [depurar un paquete de aplicación instalados](../debugger/debug-installed-app-package.md).

###  <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> Asociar al depurador a una aplicación en ejecución Windows 8.x

Si quieres asociar el depurador a una aplicación de la [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] , debes utilizar el Administrador de paquetes depurables para establecer la aplicación de modo que se ejecute en modo de depuración. El Administrador de paquetes depurables se instala con las herramientas remotas para Visual Studio.  
  
1. Instalar las herramientas remotas para Visual Studio en el dispositivo donde está instalada la aplicación. Para obtener más información, consulte [instalar las herramientas remotas](../debugger/remote-debugging.md).  
   
1. En el Windows **iniciar** pantalla, busque e inicie **Administrador de paquetes depurables**.  
   
   Se abre una ventana de PowerShell configurada correctamente para cmdlet AppxDebug.  
   
1. Especifique el identificador PackageFullName de la aplicación. 
   
   1. Para ver una lista que incluye el PackageFullName de todas las aplicaciones, escriba `Get-AppxPackage` en el símbolo del sistema de PowerShell.  
   
   1. En el símbolo del sistema de PowerShell, escriba `Enable-AppxDebug <PackageFullName>`, donde \<PackageFullName > es el identificador PackageFullName de la aplicación.  
   
1. Seleccione **Depurar** > **Asociar al proceso**.  
   
1. En el **asociar al proceso** diálogo cuadro, especifique el dispositivo remoto en el **destino de la conexión** cuadro. 
   
   Puede especificar el nombre del dispositivo, selecciónelo en la lista desplegable en el **destino de la conexión** cuadro, o bien seleccione **buscar** para encontrar el dispositivo en el **conexiones remotas** cuadro de diálogo.  
   
1. Para especificar el tipo de código que desea depurar, junto a la **adjuntar a** cuadro, seleccione **seleccione**.  
   
1. En el **Seleccionar tipo de código** cuadro de diálogo, seleccione:
   - **Determinar automáticamente el tipo de código para depurar**, o 
   - **Depurar estos tipos de código**y, a continuación, seleccione uno o varios tipos de código en la lista.  
   
1. En el **procesos disponibles** lista, seleccione el proceso para depurar la aplicación.  
   
1. Seleccione **adjuntar**.  
  
 Visual Studio asocia el depurador al proceso. La ejecución continúa hasta que se alcanza un punto de interrupción, se suspende manualmente la ejecución, se produce una excepción no controlada o la aplicación finaliza.

> [!NOTE]
> Las aplicaciones de JavaScript se ejecutan en una instancia del proceso *wwahost.exe*. Si se ejecuta más de una aplicación de JavaScript, deberá conocer el identificador numérico del proceso (PID) de la aplicación *wwahost.exe* proceso se asocie a ella.  
> 
> Es la manera más fácil asociar a la aplicación de JavaScript cerrar todas las demás aplicaciones de JavaScript. O bien, puede anotar los PID de la ejecución *wwahost.exe* procesos en Windows Task Manager antes de iniciar la aplicación. Cuando se inicia la aplicación, su *wwahost.exe* PID será lo que es diferente de los que anotó anteriormente.  

## <a name="see-also"></a>Vea también  
 [Depurar aplicaciones en Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)   