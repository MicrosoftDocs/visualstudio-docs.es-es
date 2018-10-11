---
title: Depuración remota | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: hero-article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f658c14c75f3ec0e93ed05226a8b1192d73bf478
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/09/2018
ms.locfileid: "48880726"
---
# <a name="remote-debugging"></a>Remote Debugging
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [depuración remota](https://docs.microsoft.com/visualstudio/debugger/remote-debugging).  
  
Puede depurar una aplicación de Visual Studio que se ha implementado en un equipo diferente.  Para ello, use el depurador remoto de Visual Studio  
  
 Esta información se aplica a aplicaciones de escritorio de Windows y a aplicaciones de ASP.NET.  Para obtener información acerca de la depuración remota de aplicaciones de Windows Store y aplicaciones de Azure, consulte [depuración remota en aplicaciones de Windows Store y Azure](#bkmk_winstoreAzure).  
  
## <a name="get-the-remote-tools"></a>Obtenga las herramientas remotas  
Puede descargar las herramientas remotas directamente en el dispositivo o el servidor que desea depurar, o bien pueden obtener las herramientas remotas desde el equipo host con Visual Studio instalado.

### <a name="to-download-and-install-the-remote-tools"></a>Para descargar e instalar las herramientas remotas
  
1.  En el dispositivo o servidor máquina que desea depurar (en lugar de la máquina que ejecuta Visual Studio), obtenga la versión correcta de las herramientas remotas.

    |Versión|Vínculo|Notas|
    |-|-|-|
    |Visual Studio 2015 Update 3|[Herramientas remotas](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Si se le solicite, unirse al grupo de Visual Studio Dev Essentials gratuita o solo tiene que iniciar sesión con una suscripción válida de Visual Studio. A continuación, vuelva a abrir el vínculo si es necesario. Descargar siempre la versión que coincida con el sistema operativo del dispositivo (x 86, x64 o versión ARM)|
    |Visual Studio 2015 (antigua)|[Herramientas remotas](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Si se le solicite, unirse al grupo de Visual Studio Dev Essentials gratuita o solo tiene que iniciar sesión con una suscripción válida de Visual Studio. A continuación, vuelva a abrir el vínculo si es necesario.|
    |Visual Studio 2013|[Herramientas remotas](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|Descargar página de documentación de Visual Studio 2013|
    |Visual Studio 2012|[Herramientas remotas](https://msdn.microsoft.com/library/bt727f1t(v=vs.110).aspx#BKMK_Installing_the_Remote_Tools)|Descargar página de documentación de Visual Studio 2012|
  
2.  En la página de descarga, elija la versión de las herramientas que coincida con el sistema operativo (x 86, x64 o versión ARM) y descargue las herramientas remotas.
  
    > [!IMPORTANT]
    >  Se recomienda que instalar la versión más reciente de las herramientas remotas que coincida con su versión de Visual Studio. No se recomiendan las versiones no coinciden.  
    >   
    >  Además, debe instalar las herramientas remotas que tienen la misma arquitectura que el sistema operativo en el que desee instalarlo. En otras palabras, si desea depurar una aplicación de 32 bits en un equipo remoto ejecuta un sistema operativo de 64 bits, debe instalar la versión de 64 bits de las herramientas remotas en el equipo remoto.  
  
3.  Cuando haya terminado de descargar el archivo ejecutable, siga las instrucciones para instalar la aplicación en el equipo remoto. Consulte [instrucciones de instalación](#bkmk_setup)

Si intenta copiar el depurador remoto (msvsmon.exe) en el equipo remoto y ejecutarlo, tenga en cuenta que el **Asistente para configuración de Remote Debugger** (**rdbgwiz.exe**) se instala solo al descargar la herramientas y se deba usar al Asistente para configuración más adelante, especialmente si desea que el depurador remoto para ejecutarse como un servicio. Para obtener más información, consulte [(opcional) configurar el depurador remoto como un servicio](#bkmk_configureService) a continuación.

### <a name="to-run-the-remote-debugger-from-a-file-share"></a>Para ejecutar al depurador remoto desde un recurso compartido de archivos

Puede encontrar el depurador remoto (**msvsmon.exe**) en un equipo con Visual Studio 2015 Community, Professional o Enterprise ya instalado. Para muchos escenarios, la manera más fácil de configurar la depuración remota es ejecutar al depurador remoto (msvsmon.exe) desde un recurso compartido de archivos. Para conocer las limitaciones de uso, consulte la página de Ayuda del depurador remoto (**ayuda / uso** en el depurador remoto).

1. Buscar **msvsmon.exe** en el directorio que coincida con su versión de Visual Studio. Para Visual Studio 2015:

      **Programa de programa\Microsoft Visual Studio 14.0\Common7\IDE\Remote Debugger\x86\msvsmon.exe**
      
      **Programa de programa\Microsoft Visual Studio 14.0\Common7\IDE\Remote Debugger\x64\msvsmon.exe**

2. Recurso compartido de la **Remote Debugger** carpeta en el equipo de Visual Studio.

3. En el equipo remoto, ejecute **msvsmon.exe**. Siga el [instrucciones de instalación](#bkmk_setup).

> [!TIP] 
> Para la instalación de línea de comandos y referencia de línea de comandos, consulte la página de ayuda para **msvsmon.exe** escribiendo ``msvsmon.exe /?`` en la línea de comandos en el equipo con Visual Studio instalada (o vaya a **ayuda / uso**en el depurador remoto).

  
## <a name="supported-operating-systems"></a>Sistemas operativos admitidos  
 El equipo remoto debe ejecutarse en uno de los siguientes sistemas operativos:  
  
-   Windows 10  
  
-   Windows 8 u 8.1  
  
-   Windows 7 Service Pack 1  
  
-   Windows Server 2012 o Windows Server 2012 R2  
  
-   Windows Server 2008 Service Pack 2, Windows Server 2008 R2 Service Pack 1  
  
## <a name="supported-hardware-configurations"></a>Configuraciones de hardware compatibles  
  
-   Procesador de 1.6 GHz o más rápido  
  
-   1 GB de RAM (1,5 GB si se ejecuta en una máquina virtual)  
  
-   1 GB de espacio disponible en el disco duro  
  
-   Unidad de disco duro de 5400 RPM  
  
-   Tarjeta de vídeo compatible con DirectX 9 con resolución de pantalla de 1024 x 768 o superior  
  
## <a name="network-configuration"></a>Configuración de red  
 El equipo remoto y el equipo de Visual Studio deben estar conectados a través de una red, un grupo de trabajo, un grupo en el hogar o directamente mediante un cable Ethernet. No se admite la depuración a través de Internet.  
  
## <a name="bkmk_setup"></a>Configurar el depurador remoto  
 Debe tener permisos administrativos en el equipo remoto  
  
1.  Busque la aplicación Depurador remoto. (Abra el menú Inicio y busque **Remote Debugger**.)
  
     Si se ejecuta el depurador remoto en un servidor remoto, puede haga clic en la aplicación del depurador remoto y elegir **ejecutar como administrador** (o bien, puede ejecutar el depurador remoto como servicio). Si no se está ejecutando en un servidor remoto, simplemente inícielo con normalidad.
  
3.  Al iniciar las herramientas remotas por primera vez (o antes de que se haya configurado), el **configuración de depuración remota** aparece el cuadro de diálogo.  
  
     ![RemoteDebuggerConfWizardPage](../debugger/media/remotedebuggerconfwizardpage.png "RemoteDebuggerConfWizardPage")  
  
4.  Si la API de servicio de Windows no está instalada (que solo se produce en Windows Server 2008 R2), elija el **instalar** botón.  
  
5.  Seleccione los tipos de red en los que desea usar las herramientas remotas. Debe seleccionar al menos un tipo de red. Si los equipos están conectados a través de un dominio, debe elegir el primer elemento. Si los equipos están conectados a través de un grupo de trabajo o un grupo en el hogar, debe elegir el segundo o tercer elemento según corresponda.  
  
6.  Elija **Configurar depuración remota** para configurar el firewall e iniciar la herramienta.  
  
7.  Cuando se completa la configuración, aparecerá la ventana del depurador remoto.
  
     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
     El depurador remoto ahora está esperando una conexión. Tome nota del nombre del servidor y número de puerto que se muestra, porque lo necesitará más adelante para la configuración en Visual Studio.  
  
 Cuando haya terminado la depuración y la necesidad de detener el depurador remoto, haga clic en **archivo / salir** en la ventana. Puede reiniciarlo desde el **iniciar** menú o desde la línea de comandos:  
  
 **\<Directorio de instalación de Visual Studio > \Common7\IDE\Remote Debugger\\< x86, x64 o Appx\msvsmon.exe**.  
  
## <a name="configure-the-remote-debugger"></a>Configurar el depurador remoto  
 Puede cambiar algunos aspectos de la configuración del depurador remoto tras iniciarlo por primera vez.
  
-   Para permitir que otros usuarios para conectarse al depurador remoto, elija **herramientas / permisos**. Debe tener privilegios de administrador para conceder o denegar permisos.

    > [!IMPORTANT]
    > Puede ejecutar al depurador remoto bajo una cuenta de usuario que difiere de la cuenta de usuario que está usando en el equipo de Visual Studio, pero debe agregar la cuenta de usuario diferente a los permisos del depurador remoto. 

     Como alternativa, puede iniciar el depurador remoto desde la línea de comandos con el **/ allow \<username >** parámetro: **msvsmon /Allow \< username@computer>**.
  
-   Para cambiar el modo de autenticación o el número de puerto o especificar un valor de tiempo de espera para las herramientas remotas: elija **herramientas / opciones**.  
  
     Para obtener una lista de los números de puerto que usa de forma predeterminada, consulte [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md).  
  
     > [!WARNING]
>  Puede elegir ejecutar las herramientas remotas en el Modo sin autenticación, aunque se recomienda no usar este modo. No hay ninguna seguridad de red cuando se ejecuta en este modo. Elija el modo sin autenticación solo si está seguro de que la red no presenta riesgos de tráfico malintencionado u hostil.

##  <a name="bkmk_configureService"></a> (Opcional) Configurar al depurador remoto como servicio
 Para la depuración en ASP.NET y otros entornos de servidor, debe ejecutar al depurador remoto como administrador o, si desea que siempre en ejecución, ejecute al depurador remoto como un servicio.
  
 Si desea configurar al depurador remoto como un servicio, siga estos pasos.  
  
1.  Busque el **Asistente para configuración del depurador remoto** (rdbgwiz.exe). (Esta es una aplicación independiente del Depurador remoto). Está disponible solo cuando se instalan las herramientas remotas. No se instala con Visual Studio.  
  
2.  Inicie el asistente para la configuración. Cuando aparezca la primera página, haga clic en **Siguiente**.  
  
3.  Active la casilla **Ejecutar el depurador remoto de Visual Studio 2015 como servicio** .  
  
4.  Agregue el nombre de la cuenta de usuario y la contraseña.  
  
     Puede que necesite agregar el derecho de usuario **Iniciar sesión como servicio** a esta cuenta. (Busque **Directiva de seguridad Local** (secpol.msc) en la ventana o página **Inicio** (o escriba **secpol** en el símbolo del sistema). Cuando aparezca la ventana, haga doble clic en **Asignación de derechos de usuario**y, a continuación, busque **Iniciar sesión como servicio** en el panel derecho. Haga doble clic en ella. Agregue la cuenta de usuario para el **propiedades** ventana y haga clic en **Aceptar**.) Haga clic en **siguiente**.  
  
5.  Seleccione el tipo de red con el que desea que se comuniquen las herramientas remotas. Debe seleccionar al menos un tipo de red. Si los equipos están conectados a través de un dominio, debe elegir el primer elemento. Si los equipos están conectados a través de un grupo de trabajo o un grupo en el hogar, debe elegir el segundo o tercer elemento. Haga clic en **Siguiente**.  
  
6.  Si se puede iniciar el servicio, se mostrará el mensaje **Completó correctamente el Asistente para configuración de Visual Studio Remote Debugger**. Si no se puede iniciar el servicio, se mostrará el mensaje **Error al completar el Asistente para la configuración de Visual Studio Remote Debugger**. La página también proporciona algunas sugerencias para conseguir que se inicie el servicio.  
  
7.  Haga clic en **Finalizar**.  
  
 En este momento, el depurador remoto se ejecuta como servicio. Puede comprobarlo si va a **Panel de Control / Servicios** y busca **Depurador remoto de Visual Studio 2015**.  
  
 Puede detener e iniciar el servicio del depurador remoto desde **Panel de Control / Servicios**.  

## <a name="remote-debug-an-aspnet-application"></a>Depuración remota de una aplicación de ASP.NET  
 La implementación de una aplicación de ASP.NET en un equipo remoto que ejecuta IIS consta de varios pasos, dependiendo del sistema operativo y de la versión de IIS. Para equipos remotos que ejecutan Windows Server 2008 o Windows Server 2012 que con IIS 7.5 o posterior instalado, consulte [Remote Debugging ASP.NET en un equipo de IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).
 
 Si está depurando una aplicación ASP.NET Core, consulte la sección [publicar en IIS](https://docs.asp.net/en/latest/publishing/iis.html). Pasos necesarios para publicar un núcleo de ASP.NET en IIS. Una vez que publique una aplicación ASP.NET Core correctamente, puede tener acceso remoto depurarlo [al igual que otras aplicaciones ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md), salvo que el proceso que necesita para adjuntar a es dnx.exe en lugar de w3wp.exe.

## <a name="remote-debug-a-visual-c-project"></a>Depuración remota de un proyecto de Visual C++  
 En el siguiente procedimiento, el nombre y ruta de acceso del proyecto es C:\remotetemp\MyMfc y el nombre del equipo remoto es **MJO DL**.  
  
1.  Crear una aplicación MFC denominada **mymfc.**  
  
2.  Establecer un punto de interrupción en alguna parte de la aplicación que esté fácilmente accesible, por ejemplo en **MainFrm.cpp**, al principio de `CMainFrame::OnCreate`.  
  
3.  En el Explorador de soluciones, haga doble clic en el proyecto y seleccione **propiedades**. Abra el **depuración** ficha.  
  
4.  Establecer el **depurador para iniciar** a **depurador remoto de Windows**.  
  
     ![RemoteDebuggingCPlus](../debugger/media/remotedebuggingcplus.png "RemoteDebuggingCPlus")  
  
5.  Realice los siguientes cambios de las propiedades:  
  
    |Parámetro|Valor|
    |-|-|  
    |Comando remoto|C:\remotetemp\mymfc.exe|  
    |Directorio de trabajo|C:\remotetemp|  
    |Nombre de servidor remoto|Lista de distribución MJO:*númeroDePuerto*|  
    |Conexión|Remoto con autenticación de Windows|  
    |Tipo de depurador|Solo nativo|  
    |Directorio de implementación|C:\remotetemp.|  
    |Archivos adicionales para implementar|C:\data\mymfcdata.txt.|  
  
     Si implementa archivos adicionales (opcionales), la carpeta debe existir en ambos equipos.  
  
6.  En el Explorador de soluciones, haga clic en la solución y elija **Configuration Manager**.  
  
7.  Para el **depurar** configuración, seleccione el **implementar** casilla de verificación.  
  
     ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")  
  
8.  Iniciar la depuración (**depurar / Iniciar depuración**, o **F5**).  
  
9. El archivo ejecutable se implementa automáticamente en el equipo remoto.  
  
10. Si se le solicite, escriba las credenciales de red para conectarse a la máquina remota.  
  
     Las credenciales necesarias son específicas de la configuración de seguridad de su red. Por ejemplo, en un equipo de dominio, puede elegir un certificado de seguridad o escriba su nombre de dominio y contraseña. En un equipo que no sea de dominio, puede escribir el nombre del equipo y un nombre de cuenta de usuario válido, como **MJO-DL\name@something.com**, junto con la contraseña correcta.  
  
11. En el equipo de Visual Studio, verá que la ejecución se detiene en el punto de interrupción.  
  
    > [!TIP]
    >  De manera alternativa, puede implementar los archivos como un paso independiente. En el **el Explorador de soluciones,** haga clic en el **mymfc** nodo y, a continuación, elija **implementar**.  
  
 Si tiene archivos de código que debe usar la aplicación, deberá incluirlos en el proyecto de Visual Studio. Cree una carpeta de proyecto para los archivos adicionales (en el **el Explorador de soluciones**, haga clic en **agregar / nueva carpeta**.) A continuación, agregue los archivos a la carpeta (en el **el Explorador de soluciones**, haga clic en **Add / existente elemento**, a continuación, seleccione los archivos.). En el **propiedades** para cada archivo, establezca **Copy to Output Directory** a **copiar siempre**.  
  
## <a name="remote-debug-a-visual-c-or-visual-basic-project"></a>Depuración remota de un proyecto de Visual C# o Visual Basic  
 El depurador no puede implementar aplicaciones de escritorio de Visual C# o Visual Basic en un equipo remoto, pero se pueden depurar de manera remota como se describe a continuación. El siguiente procedimiento se da por supuesto que desea depurar en un equipo denominado **MJO DL**, tal y como se muestra en la ilustración anterior.
  
1.  Cree un proyecto WPF denominado **MyWpf**.  
  
2.  Establezca un punto de interrupción en alguna parte del código fácilmente accesible.  
  
     Por ejemplo, puede establecer un punto de interrupción en un controlador de botón. Para ello, abra MainWindow.xaml y agregar un control de botón en el cuadro de herramientas, a continuación, haga doble clic en el botón para abrir su controlador.
  
3.  En el Explorador de soluciones, haga clic en el proyecto y elija **propiedades**.  
  
4.  En el **propiedades** página, elija el **depurar** ficha.  
  
     ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")  
  
5.  Asegúrese de que el **directorio de trabajo** cuadro de texto está vacío.  
  
6.  Elija **usar equipo remoto**y el tipo **MJO-DL:4020** en el cuadro de texto. (4020 es el número de puerto que se muestra en la ventana del depurador remoto).  
  
7.  Asegúrese de que **Habilitar depuración de código nativo** no está seleccionada.  
  
8.  Compile el proyecto.  
  
9. Cree una carpeta en el equipo remoto que es la misma ruta que el **depurar** carpeta del equipo de Visual Studio:  **\<ruta de acceso de origen > \MyWPF\MyWPF\bin\Debug**.  
  
10. Copie el archivo ejecutable que acaba de compilar desde el equipo de Visual Studio a la carpeta recién creada en el equipo remoto.
  
    > [!CAUTION]
    >  No realice cambios en el código o volver a generar (o debe repetir este paso). El archivo ejecutable que copió en el equipo remoto debe coincidir exactamente con el origen local y los símbolos.

    Puede copiar manualmente el proyecto, use Xcopy, Robocopy, Powershell u otras opciones.
  
11. Asegúrese de que el depurador remoto se está ejecutando en el equipo de destino. (Si no es así, busque **Remote Debugger** en el **iniciar** menú. ) En la ventana del depurador remoto tiene este aspecto.  
  
     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")  
  
12. En Visual Studio, inicie la depuración (**depurar / Iniciar depuración**, o **F5**).  
  
13. Si se le solicite, escriba las credenciales de red para conectarse a la máquina remota.  
  
     Las credenciales requeridas varían según la configuración de seguridad de su red. Por ejemplo, en un equipo de dominio, puede escribir el nombre de dominio y la contraseña. En un equipo que no sea de dominio, puede escribir el nombre del equipo y un nombre de cuenta de usuario válido, como **MJO-DL\name@something.com**, junto con la contraseña correcta.

     Verá que la ventana principal de la aplicación de WPF está abierta en el equipo remoto.
  
14. Si es necesario, tome medidas para el punto de interrupción. Debe ver que el punto de interrupción está activo. Si no lo está, quiere decir que no se han cargado los símbolos de la aplicación. Vuelva a intentar y si esto no funciona, obtener información sobre la carga de símbolos y cómo solucionarlos en [descripción de los archivos de símbolos y Visual Studio Lores](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/05/understanding-symbol-files-and-visual-studio-s-symbol-settings.aspx).
  
15. En la máquina de Visual Studio, verá que la ejecución se detiene en el punto de interrupción.
  
 Si tiene archivos de código que debe usar la aplicación, deberá incluirlos en el proyecto de Visual Studio. Cree una carpeta de proyecto para los archivos adicionales (en el **el Explorador de soluciones**, haga clic en **agregar / nueva carpeta**.) A continuación, agregue los archivos a la carpeta (en el **el Explorador de soluciones**, haga clic en **Add / existente elemento**, a continuación, seleccione los archivos.). En el **propiedades** para cada archivo, establezca **Copy to Output Directory** a **copiar siempre**.
  
## <a name="set-up-debugging-with-remote-symbols"></a>Configurar la depuración con símbolos remotos  
 Puede depurar su código con los símbolos que se generan en el equipo de Visual Studio. El rendimiento del depurador remoto es mucho mejor cuando se usan símbolos locales.  Si debe usar símbolos remotos, deberá indicar al monitor de depuración remota que busque símbolos en el equipo remoto.  
  
 A partir de Visual Studio 2013 Update 2, puede usar el siguiente modificador de línea de comandos de msvsmon para usar símbolos remotos para el código administrado: `Msvsmon / /FallbackLoadRemoteManagedPdbs`  
  
 Para obtener más información, consulte la Ayuda de depuración remota (presione **F1** en la ventana del depurador remoto, o haga clic en **ayuda / uso**). Puede encontrar más información en [remoto cargar cambios de símbolos .NET en Visual Studio 2012 y 2013](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013.aspx)  
  
##  <a name="bkmk_winstoreAzure"></a> Depuración remota en aplicaciones de Windows Store y Azure  
 Para obtener información sobre la depuración remota con las aplicaciones de Windows Store, consulte [depurar y probar aplicaciones de Windows Store en un dispositivo remoto desde Visual Studio](http://msdn.microsoft.com/library/windows/apps/hh441469.aspx).  
  
 Para obtener información sobre la depuración en Azure, consulte uno de estos temas:  
  
-   [Depurar un servicio en la nube o una máquina Virtual en Visual Studio](http://msdn.microsoft.com/library/azure/ff683670.aspx)  
  
-   [Depurar el back-end de .NET en Visual Studio](http://blogs.msdn.com/b/azuremobile/archive/2014/03/14/debugging-net-backend-in-visual-studio.aspx)  
  
-   Introducción a la depuración remota en sitios Web de Azure ([parte 1](http://azure.microsoft.com/blog/2014/05/06/introduction-to-remote-debugging-on-azure-web-sites/), [parte 2](http://azure.microsoft.com/blog/2014/05/07/introduction-to-remote-debugging-azure-web-sites-part-2-inside-remote-debugging/), [parte 3](http://azure.microsoft.com/blog/2014/05/08/introduction-to-remote-debugging-on-azure-web-sites-part-3-multi-instance-environment-and-git/)).  
  
## <a name="see-also"></a>Vea también  
 [Depurar en Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [Configurar el Firewall de Windows para la depuración remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)   
 [Depuración remota de ASP.NET en un equipo remoto de IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)  
 [Errores de la depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)



