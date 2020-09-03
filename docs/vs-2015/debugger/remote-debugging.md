---
title: Depuración remota | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "74300550"
---
# <a name="remote-debugging"></a>Depuración remota
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede depurar una aplicación de Visual Studio que se ha implementado en un equipo diferente.  Para ello, use el depurador remoto de Visual Studio  
  
 Esta información se aplica a aplicaciones de escritorio de Windows y a aplicaciones de ASP.NET.  Para obtener información sobre la depuración remota de aplicaciones de la tienda Windows y las aplicaciones de Azure, consulte [depuración remota en aplicaciones de la tienda Windows y Azure](#bkmk_winstoreAzure).  
  
## <a name="get-the-remote-tools"></a>Obtención de las herramientas remotas  
Puede descargar las herramientas remotas directamente en el dispositivo o servidor que desea depurar, o puede obtener las herramientas remotas desde el equipo host con Visual Studio instalado.

### <a name="to-download-and-install-the-remote-tools"></a>Para descargar e instalar las herramientas remotas
  
1. En el equipo del dispositivo o servidor que desea depurar (en lugar de en el equipo que ejecuta Visual Studio), obtenga la versión correcta de las herramientas remotas.

    |Versión|Vínculo|Notas|
    |-|-|-|
    |Visual Studio 2015 Update 3|[Herramientas remotas](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Si se le solicita, únase al grupo de Visual Studio Dev Essentials gratuito o simplemente inicie sesión con una suscripción válida de Visual Studio. A continuación, vuelva a abrir el vínculo si es necesario. Descargar siempre la versión que coincida con el sistema operativo del dispositivo (versión x86, x64 o ARM)|
    |Visual Studio 2015 (anterior)|[Herramientas remotas](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Si se le solicita, únase al grupo de Visual Studio Dev Essentials gratuito o simplemente inicie sesión con una suscripción válida de Visual Studio. A continuación, vuelva a abrir el vínculo si es necesario.|
    |Visual Studio 2013|[Herramientas remotas](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|Página de descarga en la documentación de Visual Studio 2013|
    |Visual Studio 2012|[Herramientas remotas](https://msdn.microsoft.com/library/bt727f1t(v=vs.110).aspx#BKMK_Installing_the_Remote_Tools)|Página de descarga de la documentación de Visual Studio 2012|
  
2. En la página de descarga, elija la versión de las herramientas que coincida con el sistema operativo (versión x86, x64 o ARM) y descargue las herramientas remotas.
  
    > [!IMPORTANT]
    > Se recomienda instalar la versión más reciente de las herramientas remotas que coincida con su versión de Visual Studio. No se recomiendan las versiones no coincidentes.  
    >   
    >  Además, debe instalar las herramientas remotas que tienen la misma arquitectura que el sistema operativo en el que desea instalarlo. En otras palabras, si desea depurar una aplicación de 32 bits en un equipo remoto que ejecuta un sistema operativo de 64 bits, debe instalar la versión de 64 bits de las herramientas remotas en el equipo remoto.  
  
3. Cuando haya terminado de descargar el archivo ejecutable, siga las instrucciones para instalar la aplicación en el equipo remoto. Vea las [instrucciones de configuración](#bkmk_setup)

Si intenta copiar el depurador remoto (msvsmon.exe) en el equipo remoto y ejecutarlo, tenga en cuenta que el **Asistente para configuración de Remote Debugger** (**rdbgwiz.exe**) solo se instala al descargar las herramientas, y es posible que necesite usar el Asistente para la configuración más adelante, especialmente si desea que el depurador remoto se ejecute como un servicio. Para obtener más información, vea [(opcional) configurar el depurador remoto como un servicio](#bkmk_configureService) a continuación.

### <a name="to-run-the-remote-debugger-from-a-file-share"></a>Para ejecutar el depurador remoto desde un recurso compartido de archivos

Puede encontrar el depurador remoto (**msvsmon.exe**) en un equipo con Visual Studio 2015 Community, Professional o Enterprise ya instalado. En muchos escenarios, la manera más sencilla de configurar la depuración remota es ejecutar el depurador remoto (msvsmon.exe) desde un recurso compartido de archivos. Para conocer las limitaciones de uso, vea la página de ayuda del Depurador remoto (**ayuda/uso** del Depurador remoto).

1. Busque **msvsmon.exe** en el directorio que coincida con su versión de Visual Studio. Para Visual Studio 2015:

      **Archivos de Programa\microsoft Visual Studio 14.0 \ Common7\IDE\Remote Debugger\x86\msvsmon.exe**
      
      **Archivos de Programa\microsoft Visual Studio 14.0 \ Common7\IDE\Remote Debugger\x64\msvsmon.exe**

2. Comparta la carpeta **Remote Debugger** en el equipo de Visual Studio.

3. En el equipo remoto, ejecute **msvsmon.exe**. Siga las [instrucciones de instalación](#bkmk_setup).

> [!TIP] 
> Para obtener una referencia de la línea de comandos y la instalación de la línea de comandos, consulte la página de ayuda de **msvsmon.exe** escribiendo ``msvsmon.exe /?`` en la línea de comandos del equipo con Visual Studio instalado (o vaya a **ayuda/uso** en el depurador remoto).

## <a name="supported-operating-systems"></a>Sistemas operativos admitidos  
 El equipo remoto debe ejecutarse en uno de los siguientes sistemas operativos:  
  
- Windows 10  
  
- Windows 8 u 8.1  
  
- Windows 7 Service Pack 1  
  
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
  
## <a name="set-up-the-remote-debugger"></a><a name="bkmk_setup"></a>Configurar el depurador remoto  
 Debe tener permisos administrativos en el equipo remoto  
  
1. Busque la aplicación Depurador remoto. (Abra el menú Inicio y busque el **Depurador remoto**).
  
    Si está ejecutando el depurador remoto en un servidor remoto, puede hacer clic con el botón secundario en la aplicación del Depurador remoto y elegir **Ejecutar como administrador** (o bien, puede ejecutar el depurador remoto como servicio). Si no lo está ejecutando en un servidor remoto, inícielo normalmente.
  
2. Al iniciar las herramientas remotas por primera vez (o antes de configurarla), aparece el cuadro diálogo de **configuración de depuración remota** .  
  
    ![RemoteDebuggerConfWizardPage](../debugger/media/remotedebuggerconfwizardpage.png "RemoteDebuggerConfWizardPage")  
  
3. Si la API del servicio de Windows no está instalada (que solo sucede en Windows Server 2008 R2), elija el botón **instalar** .  
  
4. Seleccione los tipos de red en los que desea usar las herramientas remotas. Debe seleccionar al menos un tipo de red. Si los equipos están conectados a través de un dominio, debe elegir el primer elemento. Si los equipos están conectados a través de un grupo de trabajo o un grupo en el hogar, debe elegir el segundo o tercer elemento según corresponda.  
  
5. Elija **configurar depuración remota** para configurar el Firewall e iniciar la herramienta.  
  
6. Cuando se completa la configuración, aparecerá la ventana del depurador remoto.
  
    ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
    El depurador remoto ahora está esperando una conexión. Anote el nombre del servidor y el número de puerto que se muestra, ya que lo necesitará más adelante para la configuración en Visual Studio.  
  
   Cuando haya terminado la depuración y necesite detener el depurador remoto, haga clic en **archivo/salir** en la ventana. Puede reiniciarlo desde el menú **Inicio** o desde la línea de comandos:  
  
   ** \<Visual Studio installation directory> Depurador \\ de \Common7\IDE\Remote<x86, x64 o Appx\msvsmon.exe**.  
  
## <a name="configure-the-remote-debugger"></a>Configurar el depurador remoto  
 Puede cambiar algunos aspectos de la configuración del depurador remoto tras iniciarlo por primera vez.
  
- Para permitir que otros usuarios se conecten al depurador remoto, elija **herramientas/permisos**. Debe tener privilegios de administrador para conceder o denegar permisos.

  > [!IMPORTANT]
  > Puede ejecutar el depurador remoto con una cuenta de usuario distinta de la que se usa en el equipo de Visual Studio, pero debe agregar dicha cuenta de usuario a los permisos del depurador remoto. 

   Como alternativa, puede iniciar el depurador remoto desde la línea de comandos con el parámetro ** \<username> /Allow** : **msvsmon \<username@computer> /Allow **.
  
- Para cambiar el modo de autenticación o el número de puerto, o para especificar un valor de tiempo de espera para las herramientas remotas: elija **herramientas/opciones**.  
  
   Para obtener una lista de los números de puerto que se usan de forma predeterminada, consulte [Asignaciones de puertos del depurador remoto](../debugger/remote-debugger-port-assignments.md).  
  
   > [!WARNING]
  > Puede elegir ejecutar las herramientas remotas en el Modo sin autenticación, aunque se recomienda no usar este modo. No hay ninguna seguridad de red cuando se ejecuta en este modo. Elija el modo sin autenticación solo si está seguro de que la red no presenta riesgos de tráfico malintencionado u hostil.

## <a name="optional-configure-the-remote-debugger-as-a-service"></a><a name="bkmk_configureService"></a> (Opcional) Configuración del depurador remoto como servicio
 Para la depuración en ASP.NET y en otros entornos de servidor, debe ejecutar el depurador remoto como administrador o, si quiere que siempre esté en ejecución, inicie el depurador remoto como servicio.
  
 Si quiere configurar el depurador remoto como servicio, siga estos pasos.  
  
1. Busque el **Asistente para configuración del depurador remoto** (rdbgwiz.exe). (Esta es una aplicación independiente del Depurador remoto). Está disponible solo cuando se instalan las herramientas remotas. No se instala con Visual Studio.  
  
2. Inicie el asistente para la configuración. Cuando aparezca la primera página, haga clic en **Siguiente**.  
  
3. Active la casilla **Ejecutar el depurador remoto de Visual Studio 2015 como servicio**.  
  
4. Agregue el nombre de la cuenta de usuario y la contraseña.  
  
    Puede que necesite agregar el derecho de usuario **Iniciar sesión como servicio** a esta cuenta. (Busque **Directiva de seguridad Local** (secpol.msc) en la ventana o página **Inicio** (o escriba **secpol** en el símbolo del sistema). Cuando aparezca la ventana, haga doble clic en **Asignación de derechos de usuario**y, a continuación, busque **Iniciar sesión como servicio** en el panel derecho. Haga doble clic en ella. Agregue la cuenta de usuario a la ventana **propiedades** y haga clic en **Aceptar**). Haga clic en **siguiente**.  
  
5. Seleccione el tipo de red con el que desea que se comuniquen las herramientas remotas. Debe seleccionar al menos un tipo de red. Si los equipos están conectados a través de un dominio, debe elegir el primer elemento. Si los equipos están conectados a través de un grupo de trabajo o un grupo en el hogar, debe elegir el segundo o tercer elemento. Haga clic en **Siguiente**.  
  
6. Si se puede iniciar el servicio, se mostrará el mensaje **Completó correctamente el Asistente para configuración de Visual Studio Remote Debugger**. Si no se puede iniciar el servicio, se mostrará el mensaje **Error al completar el Asistente para la configuración de Visual Studio Remote Debugger**. La página también proporciona algunas sugerencias para conseguir que se inicie el servicio.  
  
7. Haga clic en **Finalizar**.  
  
   En este momento, el depurador remoto se ejecuta como servicio. Para comprobarlo, vaya a **Panel de control/servicios** y busque **Visual Studio 2015 Remote Debugger**.  
  
   Puede detener e iniciar el servicio del Depurador remoto desde **Panel de control/servicios**.  

## <a name="remote-debug-an-aspnet-application"></a>Depuración remota de una aplicación de ASP.NET  
 La implementación de una aplicación de ASP.NET en un equipo remoto que ejecuta IIS consta de varios pasos, dependiendo del sistema operativo y de la versión de IIS. Para los equipos remotos que ejecutan Windows Server 2008 o Windows Server 2012 que tienen instalado IIS 7,5 o posterior, consulte [depuración remota ASP.net en un equipo remoto de IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).
 
 Si va a depurar una aplicación ASP.NET Core, vea [publicar en IIS](https://docs.asp.net/en/latest/publishing/iis.html). Se requieren pasos diferentes para publicar un ASP.NET Core en IIS. Una vez que publique una aplicación ASP.NET Core correctamente, puede depurarla de forma remota, al igual que [otras aplicaciones de ASP.net](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md), con la excepción de que el proceso al que debe asociarse es dnx.exe en lugar de w3wp.exe.

## <a name="remote-debug-a-visual-c-project"></a>Depuración remota de un proyecto de Visual C++  
 En el siguiente procedimiento, el nombre y la ruta de acceso del proyecto es C:\remotetemp\MyMfc, y el nombre del equipo remoto es **MJO-DL**.  
  
1. Cree una aplicación MFC denominada **mymfc**.  
  
2. Establezca un punto de interrupción en alguna parte de la aplicación que esté fácilmente accesible como, por ejemplo, en **MainFrm.cpp**, al principio de `CMainFrame::OnCreate`.  
  
3. En el Explorador de soluciones, haga clic con el botón derecho en el proyecto y seleccione **Propiedades**. Abra la pestaña **Depuración**.  
  
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
  
    Si implementa archivos adicionales (opcional), la carpeta debe existir en ambos equipos.  
  
6. En el Explorador de soluciones, haga clic con el botón derecho en la solución y elija **Administrador de configuración**.  
  
7. Para la configuración de **Depurar**, active la casilla **Implementar**.  
  
    ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")  
  
8. Iniciar depuración (depurar **/iniciar depuración**o **F5**).  
  
9. El archivo ejecutable se implementa automáticamente en el equipo remoto.  
  
10. Si se le solicita, escriba las credenciales de red para conectarse a la máquina remota.  
  
     Las credenciales necesarias son específicas de la configuración de seguridad de la red. Por ejemplo, en un equipo de dominio, puede elegir un certificado de seguridad o escribir su nombre de dominio y contraseña. En una máquina que no sea de dominio, puede escribir el nombre del equipo y un nombre de cuenta de usuario válido, como <strong>MJO-DL\name@something.com</strong>, junto con la contraseña correcta.  
  
11. En el equipo de Visual Studio, verá que la ejecución se detiene en el punto de interrupción.  
  
    > [!TIP]
    > De manera alternativa, puede implementar los archivos como un paso independiente. En el **Explorador de soluciones**, haga clic con el botón derecho en el nodo **mymfc** y después elija **Implementar**.  
  
    Si tiene archivos de código que debe usar la aplicación, deberá incluirlos en el proyecto de Visual Studio. Cree una carpeta de proyecto para los archivos adicionales (en el **Explorador de soluciones**, haga clic en **Agregar o nueva carpeta**). A continuación, agregue los archivos a la carpeta (en el **Explorador de soluciones**, haga clic en **Agregar/elemento existente**y, a continuación, seleccione los archivos). En la página **Propiedades** de cada archivo, establezca **Copiar en el directorio de resultado** en **Copiar siempre**.  
  
## <a name="remote-debug-a-visual-c-or-visual-basic-project"></a>Depuración remota de un proyecto de Visual C# o Visual Basic  
 El depurador no puede implementar aplicaciones de escritorio de Visual C# o Visual Basic en un equipo remoto, pero se pueden depurar de manera remota como se describe a continuación. En el procedimiento siguiente se da por supuesto que desea depurar en un equipo denominado **MJO-DL**, tal como se muestra en la ilustración anterior.
  
1. Cree un proyecto WPF denominado **MyWpf**.  
  
2. Establezca un punto de interrupción en alguna parte del código fácilmente accesible.  
  
    Por ejemplo, puede establecer un punto de interrupción en un controlador de botón. Para ello, abra MainWindow.xaml y agregue un control de botón desde el Cuadro de herramientas; luego, haga doble clic en el botón para abrir su controlador.
  
3. En el Explorador de soluciones, haga clic con el botón derecho en el proyecto y, luego, elija **Propiedades**.  
  
4. En la página **Propiedades**, elija la pestaña **Depurar**.  
  
    ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")  
  
5. Asegúrese de que el cuadro de texto **Directorio de trabajo** está vacío.  
  
6. Elija **usar equipo remoto**y escriba **MJO-DL: 4020** en el cuadro de texto. (4020 es el número de puerto que se muestra en la ventana del Depurador remoto).  
  
7. Asegúrese de que la opción **Habilitar la depuración de código nativo** no está seleccionada.  
  
8. Compile el proyecto.  
  
9. Cree una carpeta en el equipo remoto que tenga la misma ruta de acceso que la carpeta de **depuración** en el equipo de Visual Studio: ** \<source path> \MyWPF\MyWPF\bin\Debug**.  
  
10. Copie el archivo ejecutable que acaba de compilar desde el equipo de Visual Studio a la carpeta recién creada en el equipo remoto.
  
    > [!CAUTION]
    > No realice cambios en el código ni vuelva a realizar la compilación (o tendrá que repetir este paso). El archivo ejecutable que copió en el equipo remoto debe coincidir exactamente con el origen local y los símbolos.

    Puede copiar el proyecto manualmente, usar Xcopy, Robocopy, PowerShell u otras opciones.
  
11. Asegúrese de que el depurador remoto se está ejecutando en el equipo de destino. (Si no es así, busque el **Depurador remoto** en el menú **Inicio** . ) La ventana del Depurador remoto tiene el siguiente aspecto.  
  
     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")  
  
12. En Visual Studio, inicie la depuración (depurar **/iniciar depuración**o **F5**).  
  
13. Si se le solicita, escriba las credenciales de red para conectarse al equipo remoto.  
  
     Las credenciales necesarias varían en función de la configuración de seguridad de la red. Por ejemplo, en un equipo de dominio, puede escribir el nombre de dominio y la contraseña. En un equipo que no es de dominio, puede escribir el nombre del equipo y un nombre de cuenta de usuario válido, como <strong>MJO-DL\name@something.com</strong>, junto con la contraseña correcta.

     Verá que la ventana principal de la aplicación de WPF está abierta en el equipo remoto.
  
14. Si es necesario, tome medidas para alcanzar el punto de interrupción. Debe ver que el punto de interrupción está activo. Si no lo está, quiere decir que no se han cargado los símbolos de la aplicación. Vuelva a intentarlo y, si eso no funciona, obtenga información sobre la carga de símbolos y cómo solucionarlos a través de [los archivos de símbolos y la configuración de símbolos de Visual Studio](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/).
  
15. En la máquina de Visual Studio, verá que la ejecución se detiene en el punto de interrupción.
  
    Si tiene archivos de código que debe usar la aplicación, deberá incluirlos en el proyecto de Visual Studio. Cree una carpeta de proyecto para los archivos adicionales (en el **Explorador de soluciones**, haga clic en **Agregar o nueva carpeta**). A continuación, agregue los archivos a la carpeta (en el **Explorador de soluciones**, haga clic en **Agregar/elemento existente**y, a continuación, seleccione los archivos). En la página **Propiedades** de cada archivo, establezca **Copiar en el directorio de resultado** en **Copiar siempre**.
  
## <a name="set-up-debugging-with-remote-symbols"></a>Configurar la depuración con símbolos remotos  
 Puede depurar su código con los símbolos que se generan en el equipo de Visual Studio. El rendimiento del depurador remoto es mucho mejor cuando se usan símbolos locales.  Si debe usar símbolos remotos, deberá indicar al monitor de depuración remota que busque símbolos en el equipo remoto.  
  
 A partir de Visual Studio 2013 Update 2, puede usar el siguiente modificador de línea de comandos de msvsmon para usar símbolos remotos para el código administrado: `Msvsmon / /FallbackLoadRemoteManagedPdbs`  
  
 Para obtener más información, vea la ayuda de depuración remota (presione **F1** en la ventana del Depurador remoto o haga clic en **ayuda/uso**). Encontrará más información en [Cambios en la carga remota de símbolos .NET en Visual Studio 2012 y 2013](https://devblogs.microsoft.com/devops/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013/).  
  
## <a name="remote-debugging-on-windows-store-and-azure-apps"></a><a name="bkmk_winstoreAzure"></a> Depuración remota en aplicaciones de la tienda Windows y Azure  
 Para obtener información sobre la depuración remota con aplicaciones de la tienda Windows, vea [depurar y probar aplicaciones de la tienda Windows en un dispositivo remoto desde Visual Studio](https://msdn.microsoft.com/library/windows/apps/hh441469.aspx).  
  
 Para obtener información sobre la depuración en Azure, consulte uno de estos temas:  
  
- [Depurar un servicio en la nube o una máquina virtual en Visual Studio](../azure/vs-azure-tools-debug-cloud-services-virtual-machines.md)  
  
- [Depurar el back-end de .NET en Visual Studio](https://blogs.msdn.microsoft.com/azuremobile/2014/03/14/debugging-net-backend-in-visual-studio/)  
  
- Introducción a la depuración remota en sitios web de Azure ([parte 1](https://azure.microsoft.com/blog/2014/05/06/introduction-to-remote-debugging-on-azure-web-sites/), [parte 2](https://azure.microsoft.com/blog/2014/05/07/introduction-to-remote-debugging-azure-web-sites-part-2-inside-remote-debugging/), [parte 3](https://azure.microsoft.com/blog/2014/05/08/introduction-to-remote-debugging-on-azure-web-sites-part-3-multi-instance-environment-and-git/)).  
  
## <a name="see-also"></a>Consulte también  
 [Depurar en Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [Configurar el Firewall de Windows para la depuración remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Asignaciones de puerto del Depurador remoto](../debugger/remote-debugger-port-assignments.md)   
 [Depuración remota de ASP.NET en un equipo remoto de IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)  
 [Errores de la depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)
