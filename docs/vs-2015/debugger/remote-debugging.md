---
title: Remote Debugging | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.remote.overview
dev_langs:
- C++
- CSharp
- FSharp
- JScript
- VB
helpviewer_keywords:
- remote debugging, setup
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
caps.latest.revision: 81
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 68ebd9ab8c4f9d3cda1371d90a8da459edb1592b
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300550"
---
# <a name="remote-debugging"></a>Remote Debugging
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede depurar una aplicación de Visual Studio que se ha implementado en un equipo diferente.  Para ello, use el depurador remoto de Visual Studio  
  
 Esta información se aplica a aplicaciones de escritorio de Windows y a aplicaciones de ASP.NET.  For information about remote debugging Windows Store apps and Azure apps, see [Remote Debugging on Windows Store and Azure apps](#bkmk_winstoreAzure).  
  
## <a name="get-the-remote-tools"></a>Get the remote tools  
You can either download the remote tools directly on the device or server that you want to debug, or you can get the remote tools from your host machine with Visual Studio installed.

### <a name="to-download-and-install-the-remote-tools"></a>To download and install the remote tools
  
1. On the device or server machine that you want to debug (rather than the machine running Visual Studio), get the correct version of the remote tools.

    |Versión|Link|Notas|
    |-|-|-|
    |Visual Studio 2015 Update 3|[Herramientas remotas](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|If prompted, join the free Visual Studio Dev Essentials group or you can just sign in with a valid Visual Studio subscription. Then re-open the link if necessary. Always download the version matching your device operating system (x86, x64, or  ARM version)|
    |Visual Studio 2015 (older)|[Herramientas remotas](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|If prompted, join the free Visual Studio Dev Essentials group or you can just sign in with a valid Visual Studio subscription. Then re-open the link if necessary.|
    |Visual Studio 2013|[Herramientas remotas](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|Download page in Visual Studio 2013 documentation|
    |Visual Studio 2012|[Herramientas remotas](https://msdn.microsoft.com/library/bt727f1t(v=vs.110).aspx#BKMK_Installing_the_Remote_Tools)|Download page in Visual Studio 2012 documentation|
  
2. On the download page, choose the version of the tools that matches your operating system (x86, x64, or  ARM version) and download the remote tools.
  
    > [!IMPORTANT]
    > We recommend you install the most recent version of the remote tools that matches your version of Visual Studio. Mismatched versions are not recommended.  
    >   
    >  In addition, you must install the remote tools that have the same architecture as the operating system on which you want to install it. In other words, if you want to debug a 32-bit application on a remote computer running a 64-bit operating system, you must install the 64-bit version of the remote tools on the remote computer.  
  
3. Cuando haya terminado de descargar el archivo ejecutable, siga las instrucciones para instalar la aplicación en el equipo remoto. See [setup instructions](#bkmk_setup)

If you try to copy the remote debugger (msvsmon.exe) to the remote computer and run it, be aware that the **Remote Debugger Configuration Wizard** (**rdbgwiz.exe**) is installed only when you download the tools, and you may need to use the wizard for configuration later, especially if you want the remote debugger to run as a service. For more information, see [(Optional) Configure the remote debugger as a service](#bkmk_configureService) below.

### <a name="to-run-the-remote-debugger-from-a-file-share"></a>To run the remote debugger from a file share

You can find the remote debugger (**msvsmon.exe**) on a computer with Visual Studio 2015 Community, Professional, or Enterprise already installed. For many scenarios, the easiest way to set up remote debugging is to run the remote debugger (msvsmon.exe) from a file share. For usage limitations, see the remote debugger's Help page (**Help / Usage** in the remote debugger).

1. Find **msvsmon.exe** in the directory matching your version of Visual Studio. For Visual Studio 2015:

      **Program Files\Microsoft Visual Studio 14.0\Common7\IDE\Remote Debugger\x86\msvsmon.exe**
      
      **Program Files\Microsoft Visual Studio 14.0\Common7\IDE\Remote Debugger\x64\msvsmon.exe**

2. Share the **Remote Debugger** folder on the Visual Studio computer.

3. On the remote computer, run **msvsmon.exe**. Follow the [setup instructions](#bkmk_setup).

> [!TIP] 
> For command line installation and command line reference, see the Help page for **msvsmon.exe** by typing ``msvsmon.exe /?`` in the command line on the computer with Visual Studio installed (or go to **Help / Usage** in the remote debugger).

## <a name="supported-operating-systems"></a>Sistemas operativos admitidos  
 El equipo remoto debe ejecutarse en uno de los siguientes sistemas operativos:  
  
- Windows 10  
  
- Windows 8 u 8.1  
  
- Windows 7 Service Pack 1  
  
- Windows Server 2012 o Windows Server 2012 R2  
  
- Windows Server 2008 Service Pack 2, Windows Server 2008 R2 Service Pack 1  
  
## <a name="supported-hardware-configurations"></a>Configuraciones de hardware compatibles  
  
- Procesador de 1.6 GHz o más rápido  
  
- 1 GB de RAM (1,5 GB si se ejecuta en una máquina virtual)  
  
- 1 GB de espacio disponible en el disco duro  
  
- Unidad de disco duro de 5400 RPM  
  
- Tarjeta de vídeo compatible con DirectX 9 con resolución de pantalla de 1024 x 768 o superior  
  
## <a name="network-configuration"></a>Configuración de red  
 El equipo remoto y el equipo de Visual Studio deben estar conectados a través de una red, un grupo de trabajo, un grupo en el hogar o directamente mediante un cable Ethernet. No se admite la depuración a través de Internet.  
  
## <a name="bkmk_setup"></a>Set up the remote debugger  
 Debe tener permisos administrativos en el equipo remoto  
  
1. Busque la aplicación Depurador remoto. (Open the Start menu and search for **Remote Debugger**.)
  
    If you are running the remote debugger on a  remote server, you can right-click the Remote Debugger app and choose **Run as administrator** (Or, you can run the remote debugger as a service).If you are not running it on a remote server, just start it normally.
  
2. When you start the remote tools for the first time (or before you have configured it), the **Remote Debugging Configuration** dalog box appears.  
  
    ![RemoteDebuggerConfWizardPage](../debugger/media/remotedebuggerconfwizardpage.png "RemoteDebuggerConfWizardPage")  
  
3. If the Windows Service API is not installed (which happens only on Windows Server 2008 R2), choose the **Install** button.  
  
4. Seleccione los tipos de red en los que desea usar las herramientas remotas. Debe seleccionar al menos un tipo de red. Si los equipos están conectados a través de un dominio, debe elegir el primer elemento. Si los equipos están conectados a través de un grupo de trabajo o un grupo en el hogar, debe elegir el segundo o tercer elemento según corresponda.  
  
5. Choose **Configure remote debugging** to configure the firewall and start the tool.  
  
6. Cuando se completa la configuración, aparecerá la ventana del depurador remoto.
  
    ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
    The remote debugger is now waiting for a connection. Make a note of the server name and port number that is displayed, because you will need this later for configuration in Visual Studio.  
  
   When you are finished debugging and need to stop the remote debugger, click **File / Exit** on the window. You can restart it from the **Start** menu or from the command line:  
  
   **\<Visual Studio installation directory>\Common7\IDE\Remote Debugger\\<x86, x64, or Appx\msvsmon.exe**.  
  
## <a name="configure-the-remote-debugger"></a>Configurar el depurador remoto  
 Puede cambiar algunos aspectos de la configuración del depurador remoto tras iniciarlo por primera vez.
  
- To enable other users to connect to the remote debugger, choose **Tools / Permissions**. Debe tener privilegios de administrador para conceder o denegar permisos.

  > [!IMPORTANT]
  > You can run the remote debugger under a user account that differs from the user account you are using on the Visual Studio computer, but you must add the different user account to the remote debugger's permissions. 

   Alternatively, you can start the remote debugger from the command line with the **/allow \<username>** parameter: **msvsmon /allow \<username@computer** .
  
- To change the Authentication mode or the port number, or to specify a timeout value for the remote tools: choose **Tools / Options**.  
  
   For a listing of the port numbers used by default, see [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md).  
  
   > [!WARNING]
  > Puede elegir ejecutar las herramientas remotas en el Modo sin autenticación, aunque se recomienda no usar este modo. No hay ninguna seguridad de red cuando se ejecuta en este modo. Elija el modo sin autenticación solo si está seguro de que la red no presenta riesgos de tráfico malintencionado u hostil.

## <a name="bkmk_configureService"></a> (Optional) Configure the remote debugger as a service
 For debugging in ASP.NET and other server environments, you must either run the remote debugger as an Administrator or, if you want it always running,  run the remote debugger as a service.
  
 If you want to configure the remote debugger as a service, follow these steps.  
  
1. Busque el **Asistente para configuración del depurador remoto** (rdbgwiz.exe). (This is a separate application from the Remote Debugger.) It is available only when you install the remote tools. No se instala con Visual Studio.  
  
2. Inicie el asistente para la configuración. Cuando aparezca la primera página, haga clic en **Siguiente**.  
  
3. Active la casilla **Ejecutar el depurador remoto de Visual Studio 2015 como servicio** .  
  
4. Agregue el nombre de la cuenta de usuario y la contraseña.  
  
    Puede que necesite agregar el derecho de usuario **Iniciar sesión como servicio** a esta cuenta. (Busque **Directiva de seguridad Local** (secpol.msc) en la ventana o página **Inicio** (o escriba **secpol** en el símbolo del sistema). Cuando aparezca la ventana, haga doble clic en **Asignación de derechos de usuario**y, a continuación, busque **Iniciar sesión como servicio** en el panel derecho. Haga doble clic en ella. Add the user account to the **Properties** window and click **OK**.) Click **Next**.  
  
5. Seleccione el tipo de red con el que desea que se comuniquen las herramientas remotas. Debe seleccionar al menos un tipo de red. Si los equipos están conectados a través de un dominio, debe elegir el primer elemento. Si los equipos están conectados a través de un grupo de trabajo o un grupo en el hogar, debe elegir el segundo o tercer elemento. Haga clic en **Siguiente**.  
  
6. Si se puede iniciar el servicio, se mostrará el mensaje **Completó correctamente el Asistente para configuración de Visual Studio Remote Debugger**. Si no se puede iniciar el servicio, se mostrará el mensaje **Error al completar el Asistente para la configuración de Visual Studio Remote Debugger**. La página también proporciona algunas sugerencias para conseguir que se inicie el servicio.  
  
7. Haga clic en **Finalizar**.  
  
   En este momento, el depurador remoto se ejecuta como servicio. Puede comprobarlo si va a **Panel de Control / Servicios** y busca **Depurador remoto de Visual Studio 2015**.  
  
   Puede detener e iniciar el servicio del depurador remoto desde **Panel de Control / Servicios**.  

## <a name="remote-debug-an-aspnet-application"></a>Depuración remota de una aplicación de ASP.NET  
 La implementación de una aplicación de ASP.NET en un equipo remoto que ejecuta IIS consta de varios pasos, dependiendo del sistema operativo y de la versión de IIS. For remote computers running Windows Server 2008 or Windows Server 2012 that have IIS 7.5 or later installed, please see [Remote Debugging ASP.NET on a Remote IIS Computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).
 
 If you are debugging an ASP.NET Core app, please see [Publishing to IIS](https://docs.asp.net/en/latest/publishing/iis.html). Different steps are required to publish an ASP.NET Core on IIS. Once you publish an ASP.NET Core app successfully, you can remote debug it [just like other ASP.NET apps](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md), except that the process you need to attach to is dnx.exe instead of w3wp.exe.

## <a name="remote-debug-a-visual-c-project"></a>Depuración remota de un proyecto de Visual C++  
 In the following procedure, the name and path of the project is C:\remotetemp\MyMfc, and the name of the remote computer is **MJO-DL**.  
  
1. Cree una aplicación MFC denominada **mymfc**.  
  
2. Establezca un punto de interrupción en alguna parte de la aplicación que esté fácilmente accesible como, por ejemplo, en **MainFrm.cpp**, al principio de `CMainFrame::OnCreate`.  
  
3. In Solution Explorer, right-click on the project and select **Properties**. Abra la pestaña **Depuración**.  
  
4. Establezca el **Depurador para iniciar** en **Depurador remoto de Windows**.  
  
    ![RemoteDebuggingCPlus](../debugger/media/remotedebuggingcplus.png "RemoteDebuggingCPlus")  
  
5. Realice los siguientes cambios de las propiedades:  
  
   |Parámetro|Valor|
   |-|-|  
   |Comando remoto|C:\remotetemp\mymfc.exe|  
   |Directorio de trabajo|C:\remotetemp|  
   |Nombre de servidor remoto|MJO-DL:*portnumber*|  
   |Conexión|Remoto con autenticación de Windows|  
   |Tipo de depurador|Solo nativo|  
   |Directorio de implementación|C:\remotetemp.|  
   |Archivos adicionales para implementar|C:\data\mymfcdata.txt.|  
  
    If you deploy additional files (optional), the folder must exist on both machines.  
  
6. In Solution Explorer, right-click the solution and choose **Configuration Manager**.  
  
7. Para la configuración de **Depurar**, active la casilla **Implementar**.  
  
    ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")  
  
8. Start debugging (**Debug / Start Debugging**, or **F5**).  
  
9. El archivo ejecutable se implementa automáticamente en el equipo remoto.  
  
10. If prompted, enter network credentials to connect to the remote machine.  
  
     The required credentials are specific to your network's security configuration. For example, on a domain computer, you might choose a security certificate or enter your domain name and password. On a non-domain machine, you might enter the machine name and a valid user account name, like <strong>MJO-DL\name@something.com</strong>, along with the correct password.  
  
11. En el equipo de Visual Studio, verá que la ejecución se detiene en el punto de interrupción.  
  
    > [!TIP]
    > De manera alternativa, puede implementar los archivos como un paso independiente. En el **Explorador de soluciones**, haga clic con el botón derecho en el nodo **mymfc** y después elija **Implementar**.  
  
    Si tiene archivos de código que debe usar la aplicación, deberá incluirlos en el proyecto de Visual Studio. Create a project folder for the additional files (in the **Solution Explorer**, click **Add / New Folder**.) Then add the files to the folder (in the **Solution Explorer**, click **Add / Existing Item**, then select the files.). En la página **Propiedades** de cada archivo, establezca **Copiar en el directorio de resultado** en **Copiar siempre**.  
  
## <a name="remote-debug-a-visual-c-or-visual-basic-project"></a>Depuración remota de un proyecto de Visual C# o Visual Basic  
 El depurador no puede implementar aplicaciones de escritorio de Visual C# o Visual Basic en un equipo remoto, pero se pueden depurar de manera remota como se describe a continuación. The following procedure assumes that you want to debug it on a computer named **MJO-DL**, as shown in the earlier illustration.
  
1. Cree un proyecto WPF denominado **MyWpf**.  
  
2. Establezca un punto de interrupción en alguna parte del código fácilmente accesible.  
  
    Por ejemplo, puede establecer un punto de interrupción en un controlador de botón. To do this, open MainWindow.xaml, and add a Button control from the Toolbox, then double-click the button to open it's handler.
  
3. En el Explorador de soluciones, haga clic con el botón derecho en el proyecto y, luego, elija **Propiedades**.  
  
4. En la página **Propiedades**, elija la pestaña **Depurar**.  
  
    ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")  
  
5. Asegúrese de que el cuadro de texto **Directorio de trabajo** está vacío.  
  
6. Choose **Use remote machine**, and type **MJO-DL:4020** in the text box. (4020 is the port number shown in the remote debugger window).  
  
7. Asegúrese de que la opción **Habilitar la depuración de código nativo** no está seleccionada.  
  
8. Compile el proyecto.  
  
9. Cree una carpeta en el equipo remoto en la misma ruta de acceso que la carpeta **Depurar** del equipo de Visual Studio: **\<ruta de acceso de origen>\MyWPF\MyWPF\bin\Debug**.  
  
10. Copie el archivo ejecutable que acaba de compilar desde el equipo de Visual Studio a la carpeta recién creada en el equipo remoto.
  
    > [!CAUTION]
    > Do not make changes to the code or rebuild (or you must repeat this step). El archivo ejecutable que copió en el equipo remoto debe coincidir exactamente con el origen local y los símbolos.

    You can copy the project manually, use Xcopy, Robocopy, Powershell, or other options.
  
11. Make sure the remote debugger is running on the target machine. (If it's not, search for **Remote Debugger** in the **Start** menu. ) The remote debugger window looks like this.  
  
     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")  
  
12. In Visual Studio, start debugging (**Debug / Start Debugging**, or **F5**).  
  
13. If prompted, enter network credentials to connect to the remote machine.  
  
     The required credentials vary depending on your network's security configuration. For example, on a domain computer, you can  enter your domain name and password. On a non-domain machine, you might enter the machine name and a valid user account name, like <strong>MJO-DL\name@something.com</strong>, along with the correct password.

     Verá que la ventana principal de la aplicación de WPF está abierta en el equipo remoto.
  
14. If necessary, take action to hit the breakpoint. Debe ver que el punto de interrupción está activo. Si no lo está, quiere decir que no se han cargado los símbolos de la aplicación. Retry, and if that doesn't work, get information about loading symbols and how troubleshoot them at [Understanding symbol files and Visual Studio’s symbol settings](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/).
  
15. En la máquina de Visual Studio, verá que la ejecución se detiene en el punto de interrupción.
  
    Si tiene archivos de código que debe usar la aplicación, deberá incluirlos en el proyecto de Visual Studio. Create a project folder for the additional files (in the **Solution Explorer**, click **Add / New Folder**.) Then add the files to the folder (in the **Solution Explorer**, click **Add / Existing Item**, then select the files.). En la página **Propiedades** de cada archivo, establezca **Copiar en el directorio de resultado** en **Copiar siempre**.
  
## <a name="set-up-debugging-with-remote-symbols"></a>Configurar la depuración con símbolos remotos  
 Puede depurar su código con los símbolos que se generan en el equipo de Visual Studio. El rendimiento del depurador remoto es mucho mejor cuando se usan símbolos locales.  Si debe usar símbolos remotos, deberá indicar al monitor de depuración remota que busque símbolos en el equipo remoto.  
  
 A partir de Visual Studio 2013 Update 2, puede usar el siguiente modificador de línea de comandos de msvsmon para usar símbolos remotos para el código administrado: `Msvsmon / /FallbackLoadRemoteManagedPdbs`  
  
 For more information, please see the remote debugging help (press **F1** in the remote debugger window, or click **Help / Usage**). Encontrará más información en [Cambios en la carga remota de símbolos .NET en Visual Studio 2012 y 2013](https://devblogs.microsoft.com/devops/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013/).  
  
## <a name="bkmk_winstoreAzure"></a> Remote Debugging on Windows Store and Azure apps  
 For information about remote debugging with Windows Store apps, see [Debug and test Windows Store apps on a remote device from Visual Studio](https://msdn.microsoft.com/library/windows/apps/hh441469.aspx).  
  
 Para obtener información sobre la depuración en Azure, consulte uno de estos temas:  
  
- [Debugging a Cloud Service or Virtual Machine in Visual Studio](../azure/vs-azure-tools-debug-cloud-services-virtual-machines.md)  
  
- [Debugging the .NET Backend in Visual Studio](https://blogs.msdn.microsoft.com/azuremobile/2014/03/14/debugging-net-backend-in-visual-studio/)  
  
- Introduction to Remote Debugging on Azure Web Sites ([Part 1](https://azure.microsoft.com/blog/2014/05/06/introduction-to-remote-debugging-on-azure-web-sites/), [Part 2](https://azure.microsoft.com/blog/2014/05/07/introduction-to-remote-debugging-azure-web-sites-part-2-inside-remote-debugging/), [Part 3](https://azure.microsoft.com/blog/2014/05/08/introduction-to-remote-debugging-on-azure-web-sites-part-3-multi-instance-environment-and-git/)).  
  
## <a name="see-also"></a>Vea también  
 [Depurar en Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [Configurar el Firewall de Windows para la depuración remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)   
 [Depuración remota de ASP.NET en un equipo remoto de IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)  
 [Errores de la depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)
