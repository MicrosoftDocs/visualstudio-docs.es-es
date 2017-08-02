---
title: "Iniciar una sesi&#243;n de depuraci&#243;n para aplicaciones de la Tienda en Visual Studio (VB, C#, C++ y XAML) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.IVCAppHostRemoteDebugPageObject.MachineName"
  - "VC.Project.IVCAppHostRemoteDebugPageObject.BreakpointBehavior"
  - "VC.Project.IVCAppHostLocalDebugPageObject.GPUDebuggerTargetType"
  - "VC.Project.IVCAppHostTetheredDebugPageObject.DebuggerType"
  - "VC.Project.IVCAppHostLocalDebugPageObject.BreakpointBehavior"
  - "VC.Project.IVCAppHostRemoteDebugPageObject.LaunchApplication"
  - "VC.Project.IVCAppHostRemoteDebugPageObject.GPUDebuggerTargetType"
  - "VC.Project.IVCAppHostLocalDebugPageObject.DebuggerType"
  - "VC.Project.IVCAppHostSimulatorDebugPageObject.DebuggerType"
  - "ImmersiveProjects.Properties.Debug"
  - "VC.Project.IVCAppHostTetheredDebugPageObject.LaunchApplication"
  - "VC.Project.IVCAppHostSimulatorDebugPageObject.LaunchApplication"
  - "VC.Project.IVCAppHostSimulatorDebugPageObject.GPUDebuggerTargetType"
  - "VC.Project.IVCAppHostLocalDebugPageObject.LaunchApplication"
  - "VC.Project.IVCAppHostLocalDebugPageObject.AllowLocalNetworkLoopback"
  - "AppPackage.Properties.Debug"
  - "VC.Project.IVCAppHostRemoteDebugPageObject.Authentication"
  - "VC.Project.IVCAppHostRemoteDebugPageObject.DebuggerType"
  - "VC.Project.IVCAppHostSimulatorDebugPageObject.BreakpointBehavior"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 66ec0e79-8261-4c19-a618-3fd1b3f71bbd
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Iniciar una sesi&#243;n de depuraci&#243;n para aplicaciones de la Tienda en Visual Studio (VB, C#, C++ y XAML)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

![Se aplica a Windows y a Windows Phone](~/debugger/media/windows_and_phone_content.png "windows\_and\_phone\_content")  
  
 En este tema se describe cómo iniciar una sesión de depuración para aplicaciones de la Tienda escritas en XAML y Visual C\+\+, Visual C\# o Visual Basic. Para depurar una aplicación, hay que configurar la sesión de depuración y elegir la manera de iniciar la aplicación.  
  
> [!NOTE]
>  Para aplicaciones escritas en JavaScript y HTML, consulte [Iniciar una sesión de depuración \(JavaScript\)](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md).  
  
##  <a name="BKMK_In_this_topic"></a> En este tema  
 [Iniciar la depuración de manera sencilla](#BKMK_The_easy_way_to_start_debugging)  
  
 [Configurar la sesión de depuración](#BKMK_Configure_the_debugging_session)  
  
-   [Abrir la página de propiedades de depuración del proyecto](#BKMK_Open_the_debugging_property_page_for_the_project)  
  
-   [Elegir las opciones de configuración de compilación](#BKMK_Choose_the_build_configuration_options)  
  
-   [Elegir el destino de implementación](#BKMK_Choose_the_deployment_target)  
  
-   [Elegir el depurador utilizado](#BKMK_Choose_the_debugger_to_use)  
  
-   [(Opcional) Retrasar el inicio de la sesión de depuración](#BKMK__Optional__Delay_starting_the_debug_session)  
  
-   [(Opcional) Deshabilitar bucles invertidos de red](#BKMK__Optional__Disable_network_loopbacks)  
  
-   [(Opcional) Reinstalar la aplicación al iniciar la depuración](#BKMK__Optional__Reinstall_the_app_when_you_start_debugging)  
  
-   [(Opcional) Deshabilitar el requisito de autenticación para iniciar el depurador remoto](#BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger)  
  
 [Iniciar la sesión de depuración](#BKMK_Start_the_debugging_session)  
  
-   [Iniciar la depuración (F5)](#BKMK_Start_debugging__F5_)  
  
-   [Iniciar la depuración (F5) pero retrasar el inicio de la aplicación](#BKMK_Start_debugging__F5__but_delay_the_app_start)  
  
-   [Iniciar una aplicación instalada en el depurador](#BKMK_Start_an_installed_app_in_the_debugger)  
  
-   [Asociar el depurador a una aplicación en ejecución](#BKMK_Attach_the_debugger_to_a_running_app_)  
  
    -   [Configurar la aplicación para que se ejecute en modo de depuración](#BKMK_Set_the_app_to_run_in_debug_mode)  
  
    -   [Asociar el depurador](#BKMK_Attach_the_debugger)  
  
##  <a name="BKMK_The_easy_way_to_start_debugging"></a> Iniciar la depuración de manera sencilla  
  
1.  Abre la solución de aplicación en Visual Studio.  
  
2.  Elija F5.  
  
 Visual Studio compila e inicia la aplicación con el depurador asociado. La ejecución continúa hasta que se alcanza un punto de interrupción, se suspende manualmente la ejecución, se produce una excepción no controlada o la aplicación finaliza. Para obtener más información, consulta [Navegar por una sesión de depuración \(Xaml y C\#\)](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md).  
  
##  <a name="BKMK_Configure_the_debugging_session"></a> Configurar la sesión de depuración  
  
###  <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> Abrir la página de propiedades de depuración del proyecto  
  
1.  En el Explorador de soluciones, seleccione el proyecto. Elige **Propiedades** en el menú contextual.  
  
2.  Realiza las acciones siguientes para abrir la página de propiedades de depuración del proyecto:  
  
    -   Para aplicaciones de Visual C\# y Visual Basic, elige **Depurar**.  
  
         ![Página de propiedades de depuración del proyecto de C&#35;&#47;VB](~/debugger/media/dbg_csvb_debugpropertypage.png "DBG\_CsVb\_DebugPropertyPage")  
  
    -   Para aplicaciones de Visual C\+\+, expande el nodo **Propiedades de configuración** y, después, elige **Depuración**.  
  
         ![Página de propiedades de depuración de la aplicación de la Tienda Windows de C&#43;&#43;](~/debugger/media/dbg_cpp_debugpropertypage.png "DBG\_CPP\_DebugPropertyPage")  
  
###  <a name="BKMK_Choose_the_build_configuration_options"></a> Elegir las opciones de configuración de compilación  
  
1.  En la lista **Configuración**, elige **Debug** o **\(Active\) Debug**.  
  
2.  En la lista **Plataforma** elige la plataforma de destino para la que se va a compilar. En la mayoría de los casos la mejor opción es **Cualquier CPU** \(**Todas las plataformas** en Visual C\+\+\).  
  
###  <a name="BKMK_Choose_the_deployment_target"></a> Elegir el destino de implementación  
 ![Se aplica solo a Windows](~/debugger/media/windows_only_content.png "windows\_only\_content")  
  
 Puede implementar y depurar una aplicación de la Tienda Windows en el equipo de Visual Studio, en el simulador de Visual Studio del equipo local o en un dispositivo remoto.  
  
-   Para las aplicaciones de C\# y Visual Basic, elige el destino en la lista **Dispositivo de destino** de la página de propiedades de **Depurar** del proyecto.  
  
-   Para las aplicaciones de C\+\+, elige el destino en la lista **Depurador para iniciar** de la página de propiedades de **Depuración**:  
  
 Elige una de estas opciones:  
  
|||  
|-|-|  
|**Equipo local**|Depura la aplicación en la sesión actual en el equipo local. Consulta [Ejecutar aplicaciones de la Tienda Windows en el equipo local](../debugger/run-windows-store-apps-on-the-local-machine.md).|  
|**Simulador**|Depura la aplicación en el simulador de Visual Studio para aplicaciones de la [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]. El simulador es una ventana del escritorio que te permite depurar la funcionalidad del dispositivo \(por ejemplo, gestos táctiles y de rotación de dispositivos\) que no está disponible en el equipo local. Consulta [Ejecutar aplicaciones de la Tienda Windows en el simulador](../debugger/run-windows-store-apps-in-the-simulator.md).|  
|**Equipo remoto**|Depura la aplicación en un dispositivo que esté conectado al equipo local a través de la intranet o directamente mediante un cable Ethernet. Para depurar remotamente, Herramientas remotas de Visual Studio debe estar instalado y ejecutándose en el dispositivo remoto. Consulta [Ejecutar aplicaciones de la Tienda Windows en un equipo remoto](../debugger/run-windows-store-apps-on-a-remote-machine.md).|  
  
 Si eliges **Equipo remoto**, especifica el nombre o la dirección IP del equipo remoto de una de estas maneras:  
  
-   Escribe el nombre o la dirección IP del equipo remoto.  
  
    -   Para las aplicaciones de C\# y Visual Basic, escribe el nombre o la dirección IP en el cuadro **Equipo remoto**.  
  
    -   Para las aplicaciones de C\+\+, escribe el nombre o la dirección IP en el cuadro **Nombre de equipo**.  
  
-   Elige el equipo remoto en el cuadro de diálogo **Seleccionar conexión del depurador remoto**.  
  
     Para abrir el cuadro de diálogo:  
  
    -   Para las aplicaciones de C\# y Visual Basic, elige **Buscar**.  
  
    -   Para aplicaciones de C\+\+, elija la flecha abajo en el cuadro **Nombre de equipo** y, a continuación, **\<Buscar...\>**.  
  
     ![Cuadro de diálogo Seleccionar conexión del depurador remoto](../debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN\_SelectRemoteDebuggerDlg")  
  
    > [!NOTE]
    >  El cuadro de diálogo **Seleccionar conexión del depurador remoto** muestra los equipos que están en la subred local y los que están conectados directamente con el equipo de Visual Studio mediante un cable Ethernet. Para especificar otro equipo, escribe su nombre en el cuadro **Nombre de equipo**.  
  
 ![Se aplica solo a Windows Phone](~/debugger/media/phone_only_content.png "phone\_only\_content")  
  
 Puede implementar y depurar una aplicación de la Tienda de Windows Phone en un dispositivo o en uno de los emuladores de teléfono de Visual Studio. Seleccione el dispositivo o emulador en la lista **Dispositivo de destino**.  
  
###  <a name="BKMK_Choose_the_debugger_to_use"></a> Elegir el depurador utilizado  
 De forma predeterminada, Visual Studio depura código administrado en las aplicaciones de C\# y Visual Basic.  
  
 Para las aplicaciones de C\# y Visual Basic, puedes depurar el código de C\/C\+\+ tanto administrado como nativo de la aplicación. Activa la casilla **Habilitar depuración de código no administrado** para incluir código nativo en la sesión de depuración.  
  
 De forma predeterminada, Visual Studio depura el código nativo de la aplicación de C\+\+.  
  
 Para aplicaciones de C\+\+, puede depurar determinados tipos de código contenido en los componente de la aplicación en lugar del, o además del, código nativo. El código que se debe depurar se especifica en la lista **Tipo de depurador** de la página de propiedades de **Depuración** del proyecto de aplicación.  
  
 Elija uno de estos depuradores en la lista **Proceso de aplicación**:  
  
|||  
|-|-|  
|**Solo script**|Depura el código JavaScript de la aplicación. Se omiten el código administrado y el nativo.|  
|**Solo nativo**|Depura el código C\/C\+\+ nativo de la aplicación. Se omiten el código administrado y el de JavaScript.|  
|**Solo administrado**|Depura el código administrado de la aplicación. Se omiten el código de JavaScript y el de C\/C\+\+ nativo.|  
|**Mixto \(administrado y nativo\)**|Depura el código de C\/C\+\+ nativo y el código administrado de la aplicación. Se omite el código de JavaScript.|  
|**Solo GPU**|Depura el código de C\+\+ nativo que se ejecuta en una unidad de procesamiento gráfico \(GPU\).|  
  
 ![Se aplica solo a Windows Phone](~/debugger/media/phone_only_content.png "phone\_only\_content")  
  
 Para aplicaciones de la Tienda de Windows Phone, además puede elegir el depurador que va a usar para los procesos en segundo plano desde **Proceso de tarea en segundo plano**.  
  
###  <a name="BKMK__Optional__Delay_starting_the_debug_session"></a> \(Opcional\) Retrasar el inicio de la sesión de depuración  
 De forma predeterminada, Visual Studio inicia inmediatamente la aplicación cuando se iniciar la depuración. También puedes iniciar una sesión de depuración pero retrasar el inicio de la aplicación. Si eliges esta opción, la aplicación se inicia en el depurador cuando se inicia desde la pantalla Inicio o mediante un contrato de activación, o bien cuando la inicia otro proceso o método. También puedes retrasar el inicio de tu aplicación si deseas depurar una tarea en segundo plano cuando la propia aplicación no se está ejecutando.  
  
 Para retrasar el inicio de la aplicación, tienes estas opciones:  
  
-   Para aplicaciones de Visual C\# y Visual Basic, selecciona **No iniciar, pero depurar mi código al empezar** en la página de propiedades de **Depurar**.  
  
-   Para aplicaciones de Visual C\+\+, elige **Sí** en la lista **Iniciar aplicación** de la página de propiedades de **Depuración**.  
  
###  <a name="BKMK__Optional__Disable_network_loopbacks"></a> \(Opcional\) Deshabilitar bucles invertidos de red  
 ![Se aplica solo a Windows](~/debugger/media/windows_only_content.png "windows\_only\_content")  
  
 Por razones de seguridad, a las aplicaciones de la Tienda Windows instaladas de la manera estándar en un dispositivo no se les permite realizar llamadas de red a ese dispositivo. De forma predeterminada, la implementación de Visual Studio crea una exención respecto a esta regla para la aplicación implementada. Esta exención te permite probar procedimientos de comunicación en un mismo equipo. Antes de enviar tu aplicación a la Tienda Windows, debes probarla sin la exención.  
  
 Para quitar la exención de bucle invertido de red:  
  
-   Para aplicaciones de Visual C\# y Visual Basic, desactiva la casilla **Permitir bucle invertido de red** en la página de propiedades de **Depurar**.  
  
-   Para aplicaciones de Visual C\+\+, elige **No** en la lista **Permitir bucle invertido de red** en la página de propiedades de **Depuración**.  
  
###  <a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a> \(Opcional\) Reinstalar la aplicación al iniciar la depuración  
 Para diagnosticar problemas con la instalación y la configuración inicial de tu aplicación de Visual C\# o Visual Basic, elige **Desinstalar y volver a instalar mi paquete** en la página de propiedades de **Depurar** para volver a crear una instalación original al iniciar la depuración. Esta opción no está disponible para los proyectos de Visual C\+\+.  
  
###  <a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a> \(Opcional\) Deshabilitar el requisito de autenticación para iniciar el depurador remoto  
 ![Se aplica solo a Windows](~/debugger/media/windows_only_content.png "windows\_only\_content")  
  
 De forma predeterminada, debes proporcionar credenciales para ejecutar el depurador remoto.  
  
> [!IMPORTANT]
>  Puede elegir ejecutar el depurador remoto en el Modo sin autenticación, aunque se recomienda no usar este modo. No hay ninguna seguridad de red cuando se ejecuta en este modo. Elige el modo sin autenticación solo si estás seguro de que la red no presenta riesgos de tráfico malintencionado u hostil.  
  
 Para quitar el requisito de autenticación:  
  
1.  Para aplicaciones de Visual C\# y Visual Basic, desactiva la casilla **Usar autenticación** en la página de propiedades **Depurar**.  
  
2.  Para aplicaciones de Visual C\+\+, elige **No** en la lista **Requerir autenticación** en la página de propiedades **Depuración**.  
  
 [En este tema](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Start_the_debugging_session"></a> Iniciar la sesión de depuración  
  
###  <a name="BKMK_Start_debugging__F5_"></a> Iniciar la depuración \(F5\)  
 Al seleccionar **Iniciar depuración** \(teclado: F5\) en el menú **Depurar**, Visual Studio inicia la aplicación con el depurador asociado. La ejecución continúa hasta que se alcanza un punto de interrupción, se suspende manualmente la ejecución, se produce una excepción o la aplicación finaliza.  
  
###  <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a> Iniciar la depuración \(F5\) pero retrasar el inicio de la aplicación  
 Puedes establecer que la aplicación se ejecute en modo de depuración, pero iniciarla mediante un método que no sea el depurador. Por ejemplo, puedes depurar el inicio de tu aplicación desde el menú Inicio o depurar un proceso en segundo plano de la aplicación sin iniciarla. Si deseas retrasar el inicio de la aplicación, realiza lo siguiente:  
  
-   En la página de propiedades de **Depuración** de la aplicación \(**Depurar** en Visual C\+\+\)  
  
    -   Para aplicaciones de Visual C\# y Visual Basic, elige **No iniciar, pero depurar mi código al empezar**.  
  
    -   Para aplicaciones de Visual C\+\+, elige **Sí** en la lista **Iniciar aplicación**.  
  
-   Elija **Iniciar depuración** en el menú **Depurar** \(teclado: F5\).  
  
-   Inicia la aplicación desde el menú Inicio, un contrato de ejecución o mediante otro procedimiento.  
  
 La aplicación se inicia en modo de depuración. La ejecución continúa hasta que se alcanza un punto de interrupción, se suspende manualmente la ejecución, se produce una excepción no controlada o la aplicación finaliza.  
  
 . Para obtener más información sobre la depuración de tareas en segundo plano, consulta [Desencadenar eventos de suspensión, reanudación y en segundo plano para aplicaciones de la Tienda Windows](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).  
  
###  <a name="BKMK_Start_an_installed_app_in_the_debugger"></a> Iniciar una aplicación instalada en el depurador  
 Si inicias la depuración utilizando F5, Visual Studio compila e implementa la aplicación, establece que la aplicación se ejecute en modo de depuración y, a continuación, la inicia. Para iniciar una aplicación que ya está instalada en un dispositivo, utiliza el cuadro de diálogo Depurar paquete de aplicaciones instalado. Este procedimiento es útil si necesitas depurar una aplicación instalada desde la Tienda Windows o si tienes los archivos de origen de la aplicación pero no tienes un proyecto de Visual Studio para ella. Por ejemplo, puede que tengas un sistema de compilación personalizado que no utilice proyectos o soluciones de Visual Studio.  
  
 La aplicación puede estar instalada en el dispositivo local o en un dispositivo remoto.  Puedes iniciar la aplicación inmediatamente o establecer que se ejecute en el depurador cuando se inicie mediante otro proceso o método, por ejemplo desde el menú Inicio o mediante un contrato de activación. También puedes establecer que la aplicación se ejecute en modo de depuración cuando desees depurar un proceso en segundo plano sin iniciar la aplicación. Para obtener más información, consulta [Desencadenar eventos de suspensión, reanudación y en segundo plano para aplicaciones de la Tienda Windows](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).  
  
 Para establecer que una aplicación instalada se ejecute en modo de depuración, realiza lo siguiente:  
  
> [!NOTE]
>  La aplicación no debe estar ejecutándose al iniciar este procedimiento.  
  
1.  En el menú **Depurar**, elige **Depurar paquete de aplicaciones instalado**  
  
2.  Elige una de las opciones siguientes de la lista:  
  
    |||  
    |-|-|  
    |**Equipo local**|Depura la aplicación en la sesión actual en el equipo local. Consulta [Ejecutar aplicaciones de la Tienda Windows en el equipo local](../debugger/run-windows-store-apps-on-the-local-machine.md).|  
    |**Simulador**|Depura la aplicación en el simulador de Visual Studio para aplicaciones de la [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]. El simulador es una ventana del escritorio que te permite depurar la funcionalidad del dispositivo \(por ejemplo, gestos táctiles y de rotación de dispositivos\) que no está disponible en el equipo local. Consulta [Ejecutar aplicaciones de la Tienda Windows en el simulador](../debugger/run-windows-store-apps-in-the-simulator.md).|  
    |**Equipo remoto**|Depura la aplicación en un dispositivo que esté conectado al equipo local a través de la intranet o directamente mediante un cable Ethernet. Para depurar remotamente, las Herramientas remotas de Visual Studio deben estar instaladas y ejecutándose en el dispositivo remoto. Consulta [Ejecutar aplicaciones de la Tienda Windows en un equipo remoto](../debugger/run-windows-store-apps-on-a-remote-machine.md).|  
  
3.  Elige la aplicación en la lista **Paquetes de aplicaciones instalados**.  
  
4.  Elige el motor de depuración que deseas usar en la lista **Depurar este tipo de código**.  
  
5.  \(Opcional\). Elige **No iniciar, pero depurar mi código al empezar** para depurar la aplicación cuando se inicie mediante otro método o para depurar un proceso en segundo plano.  
  
 Cuando hagas clic en **Inicio**, la aplicación se iniciará o se establecerá que se ejecute en modo de depuración.  
  
###  <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> Asociar el depurador a una aplicación en ejecución  
 Si quieres asociar el depurador a una aplicación de la [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)], debes utilizar el Administrador de paquetes depurables para establecer la aplicación de modo que se ejecute en modo de depuración. El Administrador de paquetes depurables se instala con las Herramientas remotas de Visual Studio.  
  
 Asociar el depurador a una aplicación resulta útil si tienes que depurar una aplicación ya instalada, por ejemplo, que se haya instalado desde la [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]. Es necesario asociarlo cuando tienes los archivos de origen de la aplicación pero no tienes un proyecto de Visual Studio para ella. Por ejemplo, puede que tengas un sistema de compilación personalizado que no utilice proyectos o soluciones de Visual Studio.  
  
 Para asociar el depurador a una aplicación debes seguir estos pasos:  
  
1.  Establece la aplicación para que se ejecute en modo de depuración. Se tiene que hacer cuando la aplicación no se está ejecutando.  
  
2.  Inicia la aplicación. Puedes iniciar la aplicación desde la pantalla Inicio, un contrato de ejecución o algún otro método.  
  
3.  Asocia el depurador a la aplicación en ejecución.  
  
####  <a name="BKMK_Set_the_app_to_run_in_debug_mode"></a> Configurar la aplicación para que se ejecute en modo de depuración  
  
1.  Instala las Herramientas remotas de Visual Studio en el dispositivo donde esté instalada la aplicación. Consulte [Instalar las herramientas remotas](http://msdn.microsoft.com/library/windows/apps/hh441469.aspx#BKMK_Installing_the_Remote_Tools).  
  
2.  En la pantalla Inicio, busca `Debuggable Package Manager`. Inícialo.  
  
     Se abre una ventana de PowerShell configurada correctamente para cmdlet AppxDebug.  
  
3.  Para habilitar la depuración de una aplicación, debes especificar el identificador PackageFullName de la aplicación. Para ver una lista de todas las aplicaciones que incluyen PackageFullName, escribe `Get-AppxPackage` en el símbolo del sistema de PowerShell.  
  
4.  En el símbolo del sistema de PowerShell, especifique `Enable-AppxDebug` *PackageFullName*, donde *PackageFullName* es el identificador PackageFullName de la aplicación.  
  
####  <a name="BKMK_Attach_the_debugger"></a> Asociar el depurador  
 Para asociar el depurador:  
  
1.  En el menú **Depurar**, elija **Asociar al proceso**.  
  
     Aparecerá el cuadro de diálogo **Asociar al proceso**.  
  
2.  Para asociarlo a una aplicación de un dispositivo remoto, especifícalo en el cuadro **Calificador**. Puede realizar lo siguiente:  
  
    -   Escribir el nombre en el cuadro **Calificador**.  
  
    -   Hacer clic en la flecha abajo del cuadro **Calificador** y, después, elegir el dispositivo en una lista de dispositivos asociados previamente.  
  
    -   Elegir **Buscar** para seleccionar el dispositivo en una lista de dispositivos de la subred local.  
  
3.  Especifica el tipo de código que deseas depurar en el cuadro **Asociar a**.  
  
     Elige **Seleccionar** y realiza una de las siguientes operaciones:  
  
    -   Elige **Determinar automáticamente el tipo de código para depurar**.  
  
    -   Elige **Depurar estos tipos de código** y seleccionar uno o más tipos de la lista.  
  
4.  En la lista **Procesos disponibles**, elige el proceso de aplicación.  
  
5.  Elija **Asociar**.  
  
 Visual Studio asocia el depurador al proceso. La ejecución continúa hasta que se alcanza un punto de interrupción, se suspende manualmente la ejecución, se produce una excepción no controlada o la aplicación finaliza.  
  
 [En este tema](#BKMK_In_this_topic)  
  
## Vea también  
 [Depurar aplicaciones en Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)   
 [Navegar por una sesión de depuración \(Xaml y C\#\)](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md)