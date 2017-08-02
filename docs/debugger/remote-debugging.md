---
title: "Depuraci&#243;n remota | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "hero-article"
f1_keywords: 
  - "vs.debug.remote.overview"
dev_langs: 
  - "C++"
  - "CSharp"
  - "FSharp"
  - "JScript"
  - "VB"
helpviewer_keywords: 
  - "depuración remota, configuración"
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
caps.latest.revision: 76
caps.handback.revision: 45
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Depuraci&#243;n remota
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede depurar una aplicación de Visual Studio que se ha implementado en un equipo diferente.  Para ello, use el depurador remoto de Visual Studio  
  
 Esta información se aplica a aplicaciones de escritorio de Windows y a aplicaciones de ASP.NET.  Para obtener información sobre la depuración remota de aplicaciones de la Tienda Windows y aplicaciones de Azure, vea [Depuración remota en aplicaciones de la Tienda Windows y Azure](#bkmk_winstoreAzure).  
  
## Descargar e instalar las herramientas remotas  
 Puede descargar las herramientas remotas para la depuración en [Herramientas remotas para Visual Studio de 2015](https://www.microsoft.com/en-us/download/details.aspx?id=48155). Puede elegir entre las versiones x86, x64 y ARM de las herramientas. Cuando haya terminado de descargar el archivo ejecutable, siga las instrucciones para instalar la aplicación en el equipo remoto.  
  
 Puede descargar la versión Update 1 de las herramientas remotas en [Visual Studio 2015 Update 1](https://www.microsoft.com/en-us/download/details.aspx?id=49986&44F86079-8679-400C-BFF2-9CA5F2BCBDFC=1).  
  
> [!IMPORTANT]
>  Debe instalar la versión de las herramientas remotas que coincidan con su versión de la instalación de Visual Studio. No se admiten las versiones que no coinciden. Además, debe instalar las herramientas remotas que tengan la misma arquitectura que la aplicación que desea depurar. En otras palabras, si desea depurar una aplicación de 64 bits, debe instalar la versión de 64 bits de las herramientas remotas.  
  
 Si el equipo remoto ya tiene Visual Studio 2015 Community, Enterprise o Professional instalado, el depurador remoto \(**msvsmon.exe**\) ya está instalado, por lo que podrá iniciarlo desde su directorio:  
  
 **\<directorio de instalación de Visual Studio\>\\Common7\\IDE\\Remote Debugger\\\(x64, x86, Appx\)\\msvsmon.exe**  
  
 Sin embargo, el **Asistente para configuración del depurador remoto** \(**rdbgwiz.exe**\) se instala solo al descargar e instalar las herramientas, por lo que es posible que tenga que usarlo para la configuración más adelante, especialmente si desea que el depurador remoto se ejecute como un servicio. Para obtener más información, vea [Configurar el depurador remoto como servicio](#bkmk_configureService) a continuación.  
  
## Sistemas operativos admitidos  
 El equipo remoto debe ejecutarse en uno de los siguientes sistemas operativos:  
  
-   Windows 10  
  
-   Windows 8 u 8.1  
  
-   Windows 7 Service Pack 1  
  
-   Windows Server 2012 o Windows Server 2012 R2  
  
-   Windows Server 2008 Service Pack 2, Windows Server 2008 R2 Service Pack 1  
  
## Configuraciones de hardware compatibles  
  
-   Procesador de 1.6 GHz o más rápido  
  
-   1 GB de RAM \(1,5 GB si se ejecuta en una máquina virtual\)  
  
-   1 GB de espacio disponible en el disco duro  
  
-   Unidad de disco duro de 5400 RPM  
  
-   Tarjeta de vídeo compatible con DirectX 9 con resolución de pantalla de 1024 x 768 o superior  
  
## Configuración de red  
 El equipo remoto y el equipo de Visual Studio deben estar conectados a través de una red, un grupo de trabajo, un grupo en el hogar o directamente mediante un cable Ethernet. No se admite la depuración a través de Internet.  
  
## Configurar el depurador remoto  
 Debe tener permisos administrativos en el equipo remoto  
  
1.  Busque la aplicación Depurador remoto. Puede escribir **Depurador remoto** en el menú **Inicio**.  
  
2.  Al iniciar las herramientas remotas por primera vez \(o antes de configurarlas\), aparecerá el cuadro de diálogo **Configuración de depuración remota**.  
  
     ![RemoteDebuggerConfWizardPage](../debugger/media/remotedebuggerconfwizardpage.png "RemoteDebuggerConfWizardPage")  
  
3.  Si la API de servicio de Windows no está instalada \(lo que sucede en Windows Server 2008 R2\), elija el botón **Instalar**.  
  
4.  Seleccione los tipos de red en los que desea usar las herramientas remotas. Debe seleccionar al menos un tipo de red. Si los equipos están conectados a través de un dominio, debe elegir el primer elemento. Si los equipos están conectados a través de un grupo de trabajo o un grupo en el hogar, debe elegir el segundo o tercer elemento según corresponda.  
  
5.  Elija **Configurar depuración remota** para configurar el firewall e iniciar la herramienta.  
  
6.  Cuando se completa la configuración, aparecerá la ventana del depurador remoto.  
  
     ![RemoteDebuggerWindow](~/debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")  
  
 Puede detener el depurador remoto haciendo clic en **Archivo \/ Salir** en la ventana. Puede reiniciarlo desde el menú **Inicio** o desde la línea de comandos:  
  
 **\<directorio de instalación de Visual Studio\>\\Common7\\IDE\\Remote Debugger\\\<x86, x64 o Appx\\msvsmon.exe**.  
  
## Configurar el depurador remoto  
 Puede cambiar algunos aspectos de la configuración del depurador remoto tras iniciarlo por primera vez.  
  
-   Para permitir que otros usuarios se conecten al depurador remoto, elija **Herramientas \/ Permisos**. Debe tener privilegios de administrador para conceder o denegar permisos.  
  
-   Para cambiar el modo de autenticación o el número de puerto, o bien para especificar un valor de tiempo de espera para las herramientas remotas, elija Herramientas \/ Opciones.  
  
     Para obtener una lista de los números de puerto que se usan de forma predeterminada, vea [Asignaciones de puertos del depurador remoto](../debugger/remote-debugger-port-assignments.md).  
  
> [!WARNING]
>  Puede elegir ejecutar las herramientas remotas en el Modo sin autenticación, aunque se recomienda no usar este modo. No hay ninguna seguridad de red cuando se ejecuta en este modo. Elija el modo sin autenticación solo si está seguro de que la red no presenta riesgos de tráfico malintencionado u hostil.  
  
##  <a name="bkmk_configureService"></a> Configurar el depurador remoto como servicio  
 Para la depuración en ASP.NET y en otros entornos de servidor, debe ejecutar al depurador remoto como servicio.  
  
1.  Busque el **Asistente para configuración del depurador remoto** \(rdbgwiz.exe\). \(Esta es una aplicación independiente del Depurador remoto\). Está disponible solo cuando se instalan las herramientas remotas. No se instala con Visual Studio.  
  
2.  Inicie el asistente para la configuración. Cuando aparezca la primera página, haga clic en **Siguiente**.  
  
3.  Active la casilla **Ejecutar el depurador remoto de Visual Studio 2015 como servicio**.  
  
4.  Agregue el nombre de la cuenta de usuario y la contraseña.  
  
     Puede que necesite agregar el derecho de usuario **Iniciar sesión como servicio** a esta cuenta. \(Busque **Directiva de seguridad Local** \(secpol.msc\) en la ventana o página **Inicio** \(o escriba **secpol** en el símbolo del sistema\). Cuando aparezca la ventana, haga doble clic en **Asignación de derechos de usuario** y, a continuación, busque **Iniciar sesión como servicio** en el panel derecho. Haga doble clic en ella. Agregue la cuenta de usuario a la ventana **Propiedades** y haga clic en **Aceptar**.\) Haga clic en **Siguiente**.  
  
5.  Seleccione el tipo de red con el que desea que se comuniquen las herramientas remotas. Debe seleccionar al menos un tipo de red. Si los equipos están conectados a través de un dominio, debe elegir el primer elemento. Si los equipos están conectados a través de un grupo de trabajo o un grupo en el hogar, debe elegir el segundo o tercer elemento. Haga clic en **Siguiente**.  
  
6.  Si se puede iniciar el servicio, se mostrará el mensaje **Completó correctamente el Asistente para configuración de Visual Studio Remote Debugger**. Si no se puede iniciar el servicio, se mostrará el mensaje  **Error al completar el Asistente para la configuración de Visual Studio Remote Debugger** . La página también proporciona algunas sugerencias para conseguir que se inicie el servicio.  
  
7.  Haga clic en **Finalizar**.  
  
 En este momento, el depurador remoto se ejecuta como servicio. Puede comprobarlo si va a **Panel de Control \/ Servicios** y busca **Depurador remoto de Visual Studio 2015**.  
  
 Puede detener e iniciar el servicio del depurador remoto desde **Panel de Control \/ Servicios**.  
  
## Ejecución del depurador remoto con distintas cuentas de usuario  
 El depurador remoto se puede ejecutar con una cuenta de usuario distinta de la cuenta de usuario que se usa en el equipo de Visual Studio, pero debe agregar dicha cuenta de usuario a los permisos del depurador remoto.  
  
-   Puede iniciar el depurador remoto desde la línea de comandos con el parámetro **\/allow \<nombre de usuario\>**: **msvsmon \/allow \<username@computer\>**.  
  
-   Puede agregar el usuario a los permisos del depurador remoto \(en la ventana del depurador remoto \(**Herramientas \/ Permisos**\).  
  
## Depuración remota de un proyecto de Visual C\+\+  
 En el siguiente procedimiento, el nombre y la ruta de acceso del proyecto es C:\\remotetemp\\MyMfc y el nombre del equipo remoto es **remote1**.  
  
1.  Cree una aplicación MFC denominada **mymfc**.  
  
2.  Establezca un punto de interrupción en alguna parte de la aplicación que esté fácilmente accesible como, por ejemplo, en **MainFrm.cpp**, al principio de `CMainFrame::OnCreate`.  
  
3.  En Visual Studio, en el menú **Proyecto**, seleccione **Propiedades**. Abra la pestaña **Depuración**.  
  
4.  Establezca el **Depurador para iniciar** en **Depurador remoto de Windows**.  
  
     ![RemoteDebuggingCPlus](../debugger/media/remotedebuggingcplus.png "RemoteDebuggingCPlus")  
  
5.  Realice los siguientes cambios de las propiedades:  
  
    |||  
    |-|-|  
    |**Configuración**|**Valor**|  
    |Comando remoto|C:\\remotetemp\\mymfc.exe|  
    |Directorio de trabajo|C:\\remotetemp|  
    |Nombre de servidor remoto|remote1|  
    |Conexión|Remoto con autenticación de Windows|  
    |Tipo de depurador|Solo nativo|  
    |Directorio de implementación|C:\\remotetemp.|  
    |Archivos adicionales para implementar|C:\\data\\mymfcdata.txt.|  
  
6.  En la barra de herramientas, abra el menú **Configuración de soluciones** y elija **Administrador de configuración**.  
  
7.  Para la configuración de **Depurar**, active la casilla **Implementar**.  
  
     ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")  
  
8.  Inicie la depuración\(**Depurar \/ Iniciar depuración** o presione **F5**\).  
  
9. El archivo ejecutable se implementa automáticamente en el equipo remoto.  
  
10. En el equipo de Visual Studio, verá que la ejecución se detiene en el punto de interrupción.  
  
    > [!TIP]
    >  De manera alternativa, puede implementar los archivos como un paso independiente. En el **Explorador de soluciones**, haga clic con el botón secundario en el nodo **mymfc** y, a continuación, elija **Implementar**.  
  
 Si tiene archivos de código que debe usar la aplicación, deberá incluirlos en el proyecto de Visual Studio. Cree una carpeta de proyecto para los archivos adicionales \(en el **Explorador de soluciones**, haga clic en **Agregar \/ Nueva carpeta**.\) A continuación, agregue los archivos a la carpeta \(en el E**xplorador de soluciones**, haga clic en **Agregar \/ Elemento existente** y, a continuación, seleccione los archivos.\). En la página **Propiedades** de cada archivo, establezca **Copiar en el directorio de resultados** en **Copiar siempre**.  
  
## Depuración remota de un proyecto de Visual C\# o Visual Basic  
 El depurador no puede implementar aplicaciones de escritorio de Visual C\# o Visual Basic en un equipo remoto, pero se pueden depurar de manera remota como se describe a continuación. En el siguiente procedimiento se supone que desea depurar en un equipo denominado **remote1**.  
  
1.  Cree un proyecto WPF denominado **MyWpf**.  
  
2.  Establezca un punto de interrupción en alguna parte del código fácilmente accesible. Por ejemplo, puede establecer un punto de interrupción en un controlador de botón.  
  
3.  En el menú **Proyecto**, elija **Propiedades**.  
  
4.  En la página **Propiedades**, elija la pestaña **Depurar**.  
  
     ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")  
  
5.  Asegúrese de que el cuadro de texto **Directorio de trabajo** está vacío.  
  
6.  Elija **Usar equipo remoto** y escriba **remote1** en el cuadro de texto.  
  
7.  Asegúrese de que la opción **Habilitar la depuración de código nativo** no está seleccionada.  
  
8.  Compile el proyecto.  
  
9. Cree una carpeta en el equipo remoto en la misma ruta de acceso que la carpeta **Depurar** del equipo de Visual Studio: **\<ruta de acceso de origen\>\\MyWPF\\MyWPF\\bin\\Debug**.  
  
10. Copie el archivo ejecutable que acaba de compilar desde el equipo de Visual Studio a la carpeta recién creada en el equipo remoto.  
  
    > [!CAUTION]
    >  No realice cambios en el código ni vuelva a realizar la compilación antes de este paso. El archivo ejecutable que copió en el equipo remoto debe coincidir exactamente con el origen local y los símbolos.  
  
11. En Visual Studio, inicie la depuración\(**Depurar \/ Iniciar depuración** o presione **F5**\).  
  
12. Compruebe el punto de interrupción. Debe ver que el punto de interrupción está activo. Si no lo está, quiere decir que no se han cargado los símbolos de la aplicación. Para obtener información sobre la carga de símbolos y sobre cómo solucionar problemas con este proceso, vea [Información sobre los archivos de símbolos y la configuración de símbolos de Visual Studio](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/05/understanding-symbol-files-and-visual-studio-s-symbol-settings.aspx).  
  
13. Verá que la ventana principal de la aplicación de WPF está abierta en el equipo remoto. Realice la acción que provoca que se alcance el punto de interrupción.  
  
14. En la máquina de Visual Studio, verá que la ejecución se detiene en el punto de interrupción.  
  
 Si tiene archivos de código que debe usar la aplicación, deberá incluirlos en el proyecto de Visual Studio. Cree una carpeta de proyecto para los archivos adicionales \(en el **Explorador de soluciones**, haga clic en **Agregar \/ Nueva carpeta**.\) A continuación, agregue los archivos a la carpeta \(en el E**xplorador de soluciones**, haga clic en **Agregar \/ Elemento existente** y, a continuación, seleccione los archivos.\). En la página **Propiedades** de cada archivo, establezca **Copiar en el directorio de resultados** en **Copiar siempre**.  
  
## Depuración remota de una aplicación de ASP.NET  
 La implementación de una aplicación de ASP.NET en un equipo remoto que ejecuta IIS consta de varios pasos, dependiendo del sistema operativo y de la versión de IIS. Para equipos remotos que usan Windows 8, o posterior, o sistemas operativos Windows Server 2012 con IIS 8 \(o posterior\), vea [Publicación en IIS](https://docs.asp.net/en/latest/publishing/iis.html).  
  
 Para equipos remotos que usan Windows 7 o Windows Server 2008 con IIS 7.5 instalado, vea [Depuración ASP.NET remota en un equipo remoto de IIS 7.5](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).  
  
## Configurar la depuración con símbolos remotos  
 Puede depurar su código con los símbolos que se generan en el equipo de Visual Studio. El rendimiento del depurador remoto es mucho mejor cuando se usan símbolos locales. Si debe usar símbolos remotos, deberá indicar al monitor de depuración remota que busque símbolos en el equipo remoto.  
  
 A partir de Visual Studio 2013 Update 2, puede usar el siguiente modificador de línea de comandos de msvsmon para usar símbolos remotos para el código administrado: `Msvsmon / /FallbackLoadRemoteManagedPdbs`  
  
 Para obtener más información, vea la ayuda de depuración remota \(presione **F1** en la ventana del depurador remoto, o haga clic en **Ayuda \/ Uso**\). Encontrará más información en [Cambios en la carga remota de símbolos .NET en Visual Studio 2012 y 2013](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013.aspx)  
  
##  <a name="bkmk_winstoreAzure"></a> Depuración remota en aplicaciones de la Tienda Windows y Azure  
 Para obtener información sobre la depuración remota de las aplicaciones de la Tienda Windows, vea [Depurar y probar aplicaciones de la Tienda Windows en un dispositivo remoto desde Visual Studio](http://msdn.microsoft.com/library/windows/apps/hh441469.aspx).  
  
 Para obtener información sobre la depuración en Azure, consulte uno de estos temas:  
  
-   [Depurar un servicio en la nube o una máquina virtual en Visual Studio](http://msdn.microsoft.com/library/azure/ff683670.aspx)  
  
-   [Depurar el back\-end de .NET en Visual Studio](http://blogs.msdn.com/b/azuremobile/archive/2014/03/14/debugging-net-backend-in-visual-studio.aspx)  
  
-   Introducción a la depuración remota en sitios web de Azure \([parte 1](http://azure.microsoft.com/blog/2014/05/06/introduction-to-remote-debugging-on-azure-web-sites/), [parte 2](http://azure.microsoft.com/blog/2014/05/07/introduction-to-remote-debugging-azure-web-sites-part-2-inside-remote-debugging/), [parte 3](http://azure.microsoft.com/blog/2014/05/08/introduction-to-remote-debugging-on-azure-web-sites-part-3-multi-instance-environment-and-git/)\).  
  
## Vea también  
 [Depurar en Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [Configurar el Firewall de Windows para la depuración remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Asignaciones de puertos del depurador remoto](../debugger/remote-debugger-port-assignments.md)   
 [Depuración ASP.NET remota en un equipo remoto de IIS 7.5](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)   
 [Errores de la depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)