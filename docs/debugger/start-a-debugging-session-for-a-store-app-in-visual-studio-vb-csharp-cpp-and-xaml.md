---
title: Iniciar una sesión de depuración para una aplicación de UWP en Visual Studio | Documentos de Microsoft
ms.custom: ''
ms.date: 01/04/2018
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
ms.openlocfilehash: b298e2b17f1aa8805e0ab896c6978744c6c3bd53
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="start-a-debugging-session-for-a-uwp-app-in-visual-studio"></a>Iniciar una sesión de depuración para una aplicación de UWP en Visual Studio
  
 En este tema se describe cómo iniciar una sesión de depuración para aplicaciones UWP escritas en XAML y Visual C++, Visual C# o Visual Basic y para aplicaciones UWP escritas en HTML y JavaScript. Para depurar una aplicación, hay que configurar la sesión de depuración y elegir la manera de iniciar la aplicación.  
  
##  <a name="BKMK_The_easy_way_to_start_debugging"></a> Iniciar la depuración de manera sencilla  
  
1.  Abre la solución de aplicación en Visual Studio.  
  
2.  Elija F5.  
  
 Visual Studio compila e inicia la aplicación con el depurador asociado. La ejecución continúa hasta que se alcanza un punto de interrupción, se suspende manualmente la ejecución, se produce una excepción no controlada o la aplicación finaliza.  
  
##  <a name="BKMK_Choose_the_build_configuration_options"></a> Elegir las opciones de configuración de compilación  
  
1.   En la lista desplegable lista junto a la **Iniciar depuración** botón en el depurador **estándar** barra de herramientas, elija **depurar**.  
  
2.  En la lista **Plataforma** elige la plataforma de destino para la que se va a compilar.  
  
##  <a name="BKMK_Choose_the_deployment_target"></a> Elegir el destino de implementación  
  
Puede implementar y depurar una aplicación UWP en el equipo de Visual Studio, un dispositivo conectado, el simulador de Visual Studio en el equipo local, un dispositivo remoto o un emulador. Seleccione el destino de implementación en la lista desplegable a la derecha de la **plataforma** destino en el depurador **estándar** barra de herramientas.
  
![Seleccione un destino de implementación](../debugger/media/vsrun_select_target_device.png)  
  
Elige una de estas opciones:  
  
|||  
|-|-|  
|**Equipo local**|Depura la aplicación en la sesión actual en el equipo local.|  
|**Simulador**|Depurar la aplicación en el simulador de Visual Studio para aplicaciones UWP. El simulador es una ventana del escritorio que le permite depurar la funcionalidad del dispositivo, por ejemplo, gestos táctiles y de rotación de dispositivos, que no estén disponibles en el equipo local. Esta opción solo está disponible si la aplicación **mínima de la plataforma de destino. Versión** es menor o igual que el sistema operativo en el equipo de desarrollo. Vea [UWP ejecutar aplicaciones en el simulador](../debugger/run-windows-store-apps-in-the-simulator.md).|  
|**Equipo remoto**|Depura la aplicación en un dispositivo que esté conectado al equipo local a través de la intranet o directamente mediante un cable Ethernet. Para depurar remotamente, las herramientas remotas para Visual Studio debe estar instalado y ejecutándose en el dispositivo remoto. Vea [UWP ejecutar aplicaciones en un equipo remoto](../debugger/run-windows-store-apps-on-a-remote-machine.md).|  
|**Dispositivo**|Depurar la aplicación en un dispositivo USB conectado. El dispositivo debe ser programador desbloqueada y tener la pantalla desbloqueada.|  
|**Emulador de dispositivos móvil**|Inicie un emulador con la configuración especificada en el nombre del emulador, implementar la aplicación e inicie la depuración. Emuladores solo están disponibles en equipos de Hyper-V habilitado.|  

##  <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> Elija otras opciones de depuración  

Si tiene que configurar otras opciones de depuración, abra la página de propiedades para el proyecto.
  
1.  En el Explorador de soluciones, seleccione el proyecto. Elige **Propiedades**en el menú contextual.  
  
2.  Haga esto para abrir la página de propiedades de depuración para el proyecto:  
  
    -   Para aplicaciones de Visual C# y Visual Basic, elige **Depurar**.  
  
         ![C&#35; &#47; página de propiedades de depuración de proyecto VB](../debugger/media/dbg_csvb_debugpropertypage.png)  
  
    -   Para las aplicaciones de Visual C++ y JavaScript, expanda la **propiedades de configuración** nodo y, a continuación, elija **depuración**.  
  
         ![C&#43; &#43; página de propiedades de depuración de la aplicación UWP](../debugger/media/dbg_cpp_debugpropertypage.png)  

###  <a name="BKMK_Choose_the_debugger_to_use"></a> Elegir el depurador utilizado  
De forma predeterminada, Visual Studio depura código administrado en las aplicaciones de C# y Visual Basic. Para las aplicaciones de C# y Visual Basic, puedes depurar el código de C/C++ tanto administrado como nativo de la aplicación. En aplicaciones de C++, Visual Studio depura código nativo de forma predeterminada. En las aplicaciones de JavaScript, Visual Studio depura el script de forma predeterminada. 
  
Aplicaciones de C++ y JavaScript, puede depurar determinados tipos de código que se encuentran en los componentes de la aplicación en lugar de, o además, el código nativo. El código que se debe depurar se especifica en la lista **Tipo de depurador** de la página de propiedades de **Depuración** del proyecto de aplicación.  
  
Elija uno de estos depuradores en la lista **Proceso de aplicación** :  
  
|||  
|-|-|  
|**Solo administrado**|Depura el código administrado de la aplicación. Se omiten el código de JavaScript y el de C/C++ nativo.|  
|**Solo nativo**|Depura el código C/C++ nativo de la aplicación. Se omiten el código administrado y el de JavaScript.|  
|**Mixto (administrado y nativo)**|Depura el código de C/C++ nativo y el código administrado de la aplicación. Se omite el código de JavaScript. En los proyectos de C++, esta opción se denomina **(administrado y nativo)**.|  
|**Solo script**|Depura el código JavaScript de la aplicación. Se omiten el código administrado y el nativo.|  
|**Secuencia de comandos y nativo**|Depurar código de C o C++ nativo como código de JavaScript de la aplicación. Se omite el código administrado. Está disponible en los proyectos de C++ solo.|  
|**Solo GPU (C++ AMP)**|Depura el código de C++ nativo que se ejecuta en una unidad de procesamiento gráfico (GPU). Está disponible en los proyectos de C++ solo.|  

En aplicaciones de C# y Visual Basic, se puede establecer el mismo **el tipo de depurador** valores para las tareas en segundo plano que forman parte del proyecto.
  
###  <a name="BKMK__Optional__Delay_starting_the_debug_session"></a> (Opcional) Retrasar el inicio de la sesión de depuración  
 De forma predeterminada, Visual Studio inicia inmediatamente la aplicación cuando se iniciar la depuración. También puedes iniciar una sesión de depuración pero retrasar el inicio de la aplicación. Si eliges esta opción, la aplicación se inicia en el depurador cuando se inicia desde la pantalla Inicio o mediante un contrato de activación, o bien cuando la inicia otro proceso o método. También puedes retrasar el inicio de tu aplicación si deseas depurar una tarea en segundo plano cuando la propia aplicación no se está ejecutando.  
  
 Para retrasar el inicio de la aplicación, tienes estas opciones:  
  
-   Para aplicaciones de Visual C# y Visual Basic, selecciona **No iniciar, pero depurar mi código al empezar** en la página de propiedades de **Depurar** .  
  
-   Para las aplicaciones de Visual C++ y JavaScript, seleccione **No** desde el **Iniciar aplicación** lista el **depuración** página de propiedades.  
  
###  <a name="BKMK__Optional__Disable_network_loopbacks"></a> (Opcional) Deshabilitar bucles invertidos de red  
  
 Por motivos de seguridad, una aplicación para UWP que se instala en la manera estándar no se permite realizar llamadas de red en el dispositivo se instala en. De forma predeterminada, la implementación de Visual Studio crea una exención respecto a esta regla para la aplicación implementada. Esta exención te permite probar procedimientos de comunicación en un mismo equipo. Antes de enviar la aplicación a Microsoft Store, debe probar la aplicación sin la exención.  
  
 Para quitar la exención de bucle invertido de red:  
  
-   Para aplicaciones de Visual C# y Visual Basic, desactiva la **permitir bucle invertido de red local** casilla de verificación en la **depurar** página de propiedades.  
  
-   Para las aplicaciones de Visual C++ y JavaScript, seleccione **No** desde el **permitir bucle invertido de red Local** lista el **depuración** página de propiedades.  
  
###  <a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a> (Opcional) Reinstalar la aplicación al iniciar la depuración  
 Para diagnosticar problemas con la instalación y la configuración inicial de tu aplicación de Visual C# o Visual Basic, elige **Desinstalar y volver a instalar mi paquete** en la página de propiedades de **Depurar**  para volver a crear una instalación original al iniciar la depuración. Esta opción no está disponible para los proyectos de Visual C++ y JavaScript.  
  
###  <a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a> (Opcional) Deshabilitar el requisito de autenticación para iniciar el depurador remoto  
  
 De forma predeterminada, debe proporcionar las credenciales para ejecutar el depurador remoto cuando se selecciona **equipo remoto** como el destino de implementación.
  
> [!IMPORTANT]
>  Puede elegir ejecutar el depurador remoto sin autenticación, pero se recomienda no usar este modo. No hay ninguna seguridad de red cuando se ejecuta en este modo. No elija autenticación solo si está seguro de que la red no presenta riesgos de tráfico hostil o código malintencionado.  
  
 Para quitar el requisito de autenticación:  
  
1.  Para las aplicaciones de Visual C# y Visual Basic, seleccione **equipo remoto** como el **dispositivo de destino** en el **depurar** página de propiedades y, después, establezca **modo de autenticación**  a **ninguno** o **Universal (protocolo sin cifrar)**.
  
2.  Para las aplicaciones de Visual C++ y JavaScript, seleccione **equipo remoto** como el **dispositivo de destino** en el **depuración** página de propiedades y, después, establezca **requieren Autenticación** a **ninguno** o **Universal (protocolo sin cifrar)**.  

    **Universal (protocolo sin cifrar)** es para su uso cuando va a implementar en un dispositivo remoto. Actualmente, esto es para dispositivos de IoT, dispositivos de Xbox y HoloLens dispositivos, así como creadores de actualización o equipos más recientes. Universal (protocolo sin cifrar) sólo debe utilizarse en redes de confianza. La conexión de depuración es vulnerable a los usuarios malintencionados que pudieron interceptar y cambiar los datos que se pasan entre el desarrollo y el equipo remoto.  
  
##  <a name="BKMK_Start_the_debugging_session"></a> Iniciar la sesión de depuración  
  
###  <a name="BKMK_Start_debugging__F5_"></a> Iniciar la depuración (F5)  
 Cuando eliges **Iniciar depuración** (teclado: F5) en el **depurar** menú, Visual Studio inicia la aplicación con el depurador adjunto. La ejecución continúa hasta que se alcanza un punto de interrupción, se suspende manualmente la ejecución, se produce una excepción o la aplicación finaliza.  
  
###  <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a> Iniciar la depuración (F5) pero retrasar el inicio de la aplicación  
 Puedes establecer que la aplicación se ejecute en modo de depuración, pero iniciarla mediante un método que no sea el depurador. Por ejemplo, puede depurar el inicio de la aplicación desde el menú Inicio, o para depurar un proceso en segundo plano en la aplicación sin iniciar la aplicación. Para retrasar el inicio de la aplicación, ello:  
  
-   En el **depurar** página de propiedades de la aplicación (**depuración** en Visual C++ y JavaScript)  
  
    -   Para aplicaciones de Visual C# y Visual Basic, elige **No iniciar, pero depurar mi código al empezar**.  
  
    -   Para las aplicaciones de Visual C++ y JavaScript, seleccione **Sí** desde el **Iniciar aplicación** lista.  
  
-   Elija **Iniciar depuración** en el **depurar** menú (teclado: F5).  
  
-   Inicia la aplicación desde el menú Inicio, un contrato de ejecución o mediante otro procedimiento.  
  
 La aplicación se inicia en modo de depuración. La ejecución continúa hasta que se alcanza un punto de interrupción, se suspende manualmente la ejecución, se produce una excepción no controlada o la aplicación finaliza.  
  
 Para obtener más información sobre la depuración de tareas en segundo plano, consulte [desencadenador suspender, reanudar y eventos para aplicaciones UWP en segundo plano)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).  
  
###  <a name="BKMK_Start_an_installed_app_in_the_debugger"></a> Iniciar una aplicación instalada en el depurador  
Si inicias la depuración utilizando F5, Visual Studio compila e implementa la aplicación, establece que la aplicación se ejecute en modo de depuración y, a continuación, la inicia. Para iniciar una aplicación que ya está instalada en un dispositivo, use la **depurar paquete de aplicaciones instalado** cuadro de diálogo. Este procedimiento es útil si necesitas depurar una aplicación que se instaló desde Microsoft Store, o si tiene los archivos de origen de la aplicación, pero no tiene un proyecto de Visual Studio para la aplicación. Por ejemplo, puede que tengas un sistema de compilación personalizado que no utilice proyectos o soluciones de Visual Studio.  
  
La aplicación puede estar instalada en el dispositivo local o en un dispositivo remoto.  Puedes iniciar la aplicación inmediatamente o establecer que se ejecute en el depurador cuando se inicie mediante otro proceso o método, por ejemplo desde el menú Inicio o mediante un contrato de activación. También puedes establecer que la aplicación se ejecute en modo de depuración cuando desees depurar un proceso en segundo plano sin iniciar la aplicación. Para obtener más información, consulte [desencadenador suspender, reanudar y eventos para aplicaciones UWP en segundo plano)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).  
  
Para iniciar una aplicación instalada en el depurador, elija **depurar**, a continuación, **otros destinos de depuración**y, a continuación, **depurar paquete de aplicaciones instalado**. Para obtener instrucciones, consulte [depurar un paquete de aplicación instalados](../debugger/debug-installed-app-package.md).

###  <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> Asociar al depurador a una aplicación UWP en ejecución  

Para depurar una aplicación UWP en ejecución, elija **depurar**, a continuación, **otros destinos de depuración**y, a continuación, **depurar paquete de aplicaciones instalado**. Para obtener instrucciones, consulte [depurar un paquete de aplicación instalados](../debugger/debug-installed-app-package.md).
  
###  <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> Asociar al depurador a una aplicación en ejecución Windows 8.x
 Si quieres asociar el depurador a una aplicación de la [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] , debes utilizar el Administrador de paquetes depurables para establecer la aplicación de modo que se ejecute en modo de depuración. El Administrador de paquetes depurables se instala con las herramientas remotas para Visual Studio.  
  
 Asociar el depurador a una aplicación resulta útil si tienes que depurar una aplicación ya instalada, por ejemplo, que se haya instalado desde la [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]. Es necesario asociarlo cuando tienes los archivos de origen de la aplicación pero no tienes un proyecto de Visual Studio para ella. Por ejemplo, puede que tengas un sistema de compilación personalizado que no utilice proyectos o soluciones de Visual Studio.  
  
 Para asociar el depurador a una aplicación debes seguir estos pasos:  
  
1.  Establece la aplicación para que se ejecute en modo de depuración. Se tiene que hacer cuando la aplicación no se está ejecutando.  
  
2.  Inicia la aplicación. Puedes iniciar la aplicación desde la pantalla Inicio, un contrato de ejecución o algún otro método.  
  
3.  Asocia el depurador a la aplicación en ejecución.  
  
####  <a name="BKMK_Set_the_app_to_run_in_debug_mode"></a> Configurar la aplicación para que se ejecute en modo de depuración  
  
1.  Instalar las herramientas remotas para Visual Studio en el dispositivo donde esté instalada la aplicación. Vea [instalar las herramientas remotas](../debugger/remote-debugging.md).  
  
2.  En la pantalla Inicio, busca `Debuggable Package Manager` . Inícialo.  
  
     Se abre una ventana de PowerShell configurada correctamente para cmdlet AppxDebug.  
  
3.  Para habilitar la depuración de una aplicación, debes especificar el identificador PackageFullName de la aplicación. Para ver una lista de todas las aplicaciones que incluyen PackageFullName, escribe `Get-AppxPackage` en el símbolo del sistema de PowerShell.  
  
4.  En el símbolo del sistema de PowerShell, especifique `Enable-AppxDebug` *PackageFullName* , donde *PackageFullName* es el identificador PackageFullName de la aplicación.  
  
####  <a name="BKMK_Attach_the_debugger"></a> Asociar el depurador  
 Para asociar el depurador:  
  
1.  En el menú **Depurar** , elija **Asociar al proceso**.  
  
     Aparecerá el cuadro de diálogo **Asociar al proceso** .  
  
2.  Para asociarlo a una aplicación de un dispositivo remoto, especifícalo en el cuadro **Calificador** . Puede realizar lo siguiente:  
  
    -   Escribir el nombre en el cuadro **Calificador** .  
  
    -   Hacer clic en la flecha abajo del cuadro **Calificador** y, después, elegir el dispositivo en una lista de dispositivos asociados previamente.  
  
    -   Elegir **Buscar** para seleccionar el dispositivo en una lista de dispositivos de la subred local.  
  
3.  Especifica el tipo de código que deseas depurar en el cuadro **Asociar a** .  
  
     Elige **Seleccionar** y realiza una de las siguientes operaciones:  
  
    -   Elige **Determinar automáticamente el tipo de código para depurar**.  
  
    -   Elige **Depurar estos tipos de código** y seleccionar uno o más tipos de la lista.  
  
4.  En la lista **Procesos disponibles**  , elige el proceso de aplicación.  

    > [!NOTE]
    >  A diferencia de otros tipos de aplicaciones, aplicaciones de JavaScript se ejecutan en una instancia del proceso wwahost.exe. Si hay otras aplicaciones de JavaScript ejecutándose durante la asociación, debe conocer el identificador numérico del proceso (PID) del proceso wwahost.exe en el que se ejecuta la aplicación.  
    >   
    >  El modo más fácil de solucionarlo es cerrar las demás aplicaciones de JavaScript. De lo contrario, puede abrir el Administrador de tareas de Windows antes de iniciar la aplicación y apuntar los identificadores de los procesos wwahost.exe. Cuando se especifica el proceso de asociación en el **procesos disponibles** cuadro de diálogo, wwahost.exe de la aplicación tendrá un identificador que es diferente de los demás que haya anotado.  
  
5.  Elija **Asociar**.  
  
 Visual Studio asocia el depurador al proceso. La ejecución continúa hasta que se alcanza un punto de interrupción, se suspende manualmente la ejecución, se produce una excepción no controlada o la aplicación finaliza.  
  
## <a name="see-also"></a>Vea también  
 [Depurar aplicaciones en Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)   