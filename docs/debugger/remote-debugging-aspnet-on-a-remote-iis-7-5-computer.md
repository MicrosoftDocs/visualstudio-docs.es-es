---
title: Depuración remota de ASP.NET en un equipo de IIS
ms.custom:
- remotedebugging
- seodec18
ms.date: 05/21/2018
ms.topic: conceptual
ms.assetid: 9cb339b5-3caf-4755-aad1-4a5da54b2a23
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 86b035164c4d34f4ce0182ea51fdfe6381ad2d4f
ms.sourcegitcommit: 08c144d290da373df841f04fc799e3133540a541
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/17/2019
ms.locfileid: "72536021"
---
# <a name="remote-debug-aspnet-on-a-remote-iis-computer"></a>Depuración remota de ASP.NET en un equipo remoto de IIS
Para depurar una aplicación de ASP.NET que se ha implementado en IIS, instale y ejecute las herramientas remotas en el equipo donde ha implementado la aplicación y, a continuación, asócielas a la aplicación en ejecución desde Visual Studio.

![Componentes del depurador remoto](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

En esta guía se explica cómo configurar una aplicación de ASP.NET MVC 4.5.2 de Visual Studio, implementarla en IIS y agregar el depurador remoto de Visual Studio.

> [!NOTE]
> Para depurar de forma remota ASP.NET Core en su lugar, consulte [Depuración remota de ASP.NET Core en un equipo de IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md). Para Azure App Service, puede realizar la implementación y depuración fácilmente en una instancia preconfigurada de IIS mediante [Snapshot Debugger](../debugger/debug-live-azure-applications.md) (se requiere .NET 4.6.1) o [asociando el depurador del Explorador de servidores](../debugger/remote-debugging-azure.md).

## <a name="prerequisites"></a>Requisitos previos

::: moniker range=">=vs-2019"
Para seguir los pasos que se muestran en este artículo, se requiere Visual Studio 2019.
::: moniker-end
::: moniker range="vs-2017"
Para seguir los pasos que se muestran en este artículo, se requiere Visual Studio 2017.
::: moniker-end

Estos procedimientos se han probado en estas configuraciones de servidor:
* Windows Server 2012 R2 e IIS 8 (para Windows Server 2008 R2, los pasos del servidor son diferentes)

## <a name="network-requirements"></a>Requisitos de red

El depurador remoto es compatible con Windows Server a partir de Windows Server 2008 Service Pack 2. Para obtener una lista completa de los requisitos, vea [Requisitos](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> La depuración entre dos equipos conectados a través de un proxy no se admite. La depuración a través de una conexión de latencia alta o de ancho de banda bajo, como Internet mediante acceso telefónico o Internet a través de países, no se recomienda y puede producir un error o ser inaceptablemente lento.

## <a name="app-already-running-in-iis"></a>¿La aplicación ya se está ejecutando en IIS?

En este artículo se incluyen los pasos para realizar una configuración básica de IIS en Windows Server e implementar la aplicación desde Visual Studio. Estos pasos se incluyen para garantizar que el servidor tenga instalados los componentes necesarios, que la aplicación se pueda ejecutar correctamente y que usted esté a punto para la depuración remota.

* Si la aplicación se ejecuta en IIS y solo quiere descargar el depurador remoto e iniciar la depuración, vaya a [Descargar e instalar las herramientas remotas en Windows Server](#BKMK_msvsmon).

* Si quiere obtener ayuda para asegurarse de que la aplicación esté configurada, implementada y se ejecuté correctamente en IIS para poder realizar la depuración, siga todos los pasos de este tema.

## <a name="create-the-aspnet-452-application-on-the-visual-studio-computer"></a>Creación de la aplicación de ASP.NET 4.5.2 en el equipo de Visual Studio

1. Cree una nueva aplicación de MVC ASP.NET

    ::: moniker range=">=vs-2019"
    En Visual Studio 2019, presione **Ctrl+Q** para abrir el cuadro de búsqueda, escriba **asp.net**, elija **Plantillas** y, luego, **Crear una aplicación web ASP.NET (.NET Framework)** . En el cuadro de diálogo que se muestra, asigne el nombre **MyASPApp** al proyecto y elija **Crear**. Seleccione **MVC** y **Crear**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Para hacerlo en Visual Studio 2017, elija **Archivo > Nuevo > Proyecto** y **Visual C# > Web > Aplicación web ASP.NET**. En la sección de plantillas **ASP.NET 4.5.2**, seleccione **MVC**. Asegúrese de que la opción **Habilitar compatibilidad con Docker** no esté seleccionada y de que la opción **Autenticación** esté establecida en **Sin autenticación**. Asigne el nombre **MyASPApp** al proyecto.
    ::: moniker-end

2. Abra el archivo *HomeController.cs* y establezca un punto de interrupción en el método `About()`.

## <a name="install-and-configure-iis-on-windows-server"></a><a name="bkmk_configureIIS"></a> Instalación y configuración de IIS en Windows Server

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Actualización de la configuración de seguridad del explorador en Windows Server

Si la opción Configuración de seguridad mejorada está habilitada en Internet Explorer (lo está de forma predeterminada), es posible que tenga que agregar algunos dominios como sitios de confianza para poder descargar algunos de los componentes del servidor web. Para agregar los sitios de confianza, vaya a **Opciones de Internet > Seguridad > Sitios de confianza > Sitios**. Agregue los dominios siguientes.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

Al descargar el software, es posible que reciba solicitudes para conceder permiso con el fin de cargar varios scripts y recursos de los sitios web. Algunos de estos recursos no son necesarios, pero, para simplificar el proceso, haga clic en **Agregar** cuando se le solicite.

## <a name="install-aspnet-45-on-windows-server"></a><a name="BKMK_deploy_asp_net"></a> Instalación de ASP.NET 4.5 en Windows Server

Si quiere obtener información más detallada para instalar ASP.NET en IIS, consulte [IIS 8.0 con ASP.NET 3.5 y ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

1. En el panel de la izquierda del Administrador del servidor, seleccione **IIS**. Haga clic con el botón derecho en el servidor y seleccione **Administrador de Internet Information Services (IIS)** .

1. Use el Instalador de plataforma web (WebPI) para instalar ASP.NET 4.5; desde el nodo de servidor en Windows Server 2012 R2, elija **Obtener nuevos componentes de plataforma web** y busque ASP.NET.

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg_iis_aspnet_45.png "RemoteDBG_IIS_AspNet_45")

    > [!NOTE]
    > Si usa Windows Server 2008 R2, instale ASP.NET 4 en su lugar con este comando:

     **C:\Windows\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -ir**

2. Reinicie el sistema (o ejecute **net stop was /y** seguido de **net start w3svc** desde un símbolo del sistema para obtener un cambio en la ruta de acceso del sistema).

## <a name="choose-a-deployment-option"></a>Elección de una opción de implementación

Si necesita ayuda para implementar la aplicación en IIS, tenga en cuenta estas opciones:

* Para la implementación, cree un archivo de configuración de publicación en IIS e importe la configuración en Visual Studio. En algunos escenarios, es una manera rápida de implementar la aplicación. Al crear el archivo de configuración de publicación, los permisos se configuran de forma automática en IIS.

* Para la implementación, efectúe la publicación en una carpeta local y copie la salida mediante un método preferido en una carpeta de aplicación preparada en IIS.

## <a name="optional-deploy-using-a-publish-settings-file"></a>(Opcional) Implementación mediante un archivo de configuración de publicación

Puede usar esta opción para crear un archivo de configuración de publicación e importarlo en Visual Studio.

> [!NOTE]
> Este método de implementación usa Web Deploy. Si quiere configurar Web Deploy de forma manual en Visual Studio en lugar de importar la configuración, puede instalar Web Deploy 3.6 en lugar de Web Deploy 3.6 para servidores de hospedaje. Pero si configura Web Deploy de forma manual, tendrá que asegurarse de que una carpeta de aplicación del servidor esté configurada con los valores y permisos correctos; vea [Instalación de ASP.NET 4.5 en Windows Server](#BKMK_deploy_asp_net).

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Instalación y configuración de Web Deploy para servidores de hospedaje en Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Crear el archivo de configuración de publicación en IIS en Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importar la configuración de publicación a Visual Studio e implementar

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Después de que se implemente la aplicación correctamente, debería iniciarse automáticamente. Si la aplicación no se inicia desde Visual Studio, iníciela en IIS.

1. En el cuadro de diálogo **Configuración**, haga clic en **Siguiente** para habilitar la depuración, elija una configuración de **Depuración** y, luego, **Quitar archivos adicionales en destino** en las **Opciones de publicación de archivos**.

    > [!NOTE]
    > Si elige una configuración de versión, deshabilite la depuración en el archivo *web.config* al realizar la publicación.

1. Haga clic en **Guardar** y, después, vuelva a publicar la aplicación.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(Opcional) Implementación mediante la publicación en una carpeta local

Puede usar esta opción para implementar la aplicación si quiere copiarla en IIS con PowerShell o RoboCopy, o si quiere copiar manualmente los archivos.

### <a name="configure-the-aspnet-web-site-on-the-windows-server-computer"></a><a name="BKMK_deploy_asp_net"></a> Configuración del sitio web de ASP.NET Core en el equipo con Windows Server

1. Abra el Explorador de Windows y cree una carpeta, **C:\Publish**, donde más adelante implementará el proyecto de ASP.NET.

2. Si todavía no está abierto, abra el nodo **Administrador de Internet Information Services (IIS)** . (En el panel de la izquierda del Administrador del servidor, seleccione **IIS**. Haga clic con el botón derecho en el servidor y seleccione **Administrador de Internet Information Services (IIS)** ).

3. En el panel de la izquierda, bajo **Conexiones**, vaya a **Sitios**.

4. Seleccione **Sitio web predeterminado**, elija **Configuración básica** y establezca la **Ruta de acceso física** en **C:\Publish**.

5. Haga clic con el botón secundario en el nodo **Sitio web predeterminado** y seleccione **Agregar aplicación**.

6. Establezca el campo **Alias** en **MyASPApp**, acepte el grupo de aplicaciones predeterminado (**DefaultAppPool**) y establezca la **Ruta de acceso física** en **C:\Publish**.

7. En **Conexiones**, seleccione **Grupos de aplicaciones**. Abra **DefaultAppPool** y establezca el campo Grupo de aplicaciones en **ASP.NET v4.0** (ASP.NET 4.5 no es una opción para el grupo de aplicaciones).

8. Con el sitio seleccionado en el Administrador de IIS, elija **Editar permisos** y asegúrese de que IUSR, IIS_IUSRS o el usuario configurado para el acceso a la aplicación web sea un usuario autorizado con permisos de lectura y ejecución. Si ninguno de estos usuarios está presente, agregue IUSR como usuario con permisos de lectura y ejecución.

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Publicación e implementación de la aplicación mediante la publicación en una carpeta local desde Visual Studio

También puede publicar e implementar la aplicación con el sistema de archivos u otras herramientas.

1. (ASP.NET 4.5.2) Asegúrese de que el archivo web.config muestre la versión correcta de .NET.  Por ejemplo, si tiene como destino ASP.NET 4.5.2, asegúrese de que esta versión aparezca en web.config.

    ```xml
    <system.web>
      <compilation debug="true" targetFramework="4.5.2" />
      <httpRuntime targetFramework="4.5.2" />
      <httpModules>
        <add name="ApplicationInsightsWebTracking" type="Microsoft.ApplicationInsights.Web.ApplicationInsightsHttpModule, Microsoft.AI.Web" />
      </httpModules>
    </system.web>

    ```

    Por ejemplo, la versión debe ser la 4.0 si instala ASP.NET 4 en lugar de 4.5.2.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="download-and-install-the-remote-tools-on-windows-server"></a><a name="BKMK_msvsmon"></a> Descarga e instalación de las herramientas remotas en Windows Server

Descargue la versión de las herramientas remotas que corresponda a su versión de Visual Studio.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="set-up-the-remote-debugger-on-windows-server"></a><a name="BKMK_setup"></a> Establecimiento del depurador remoto en Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Si tiene que agregar permisos para usuarios adicionales, cambiar el modo de autenticación o el número de puerto para el depurador remoto, vea [Configuración del depurador remoto](../debugger/remote-debugging.md#configure_msvsmon).

Para obtener información sobre cómo ejecutar el depurador remoto como servicio, vea [Configuración del depurador remoto como servicio](../debugger/remote-debugging.md#bkmk_configureService).

## <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a><a name="BKMK_attach"></a> Adjuntar elementos a la aplicación ASP.NET desde el equipo de Visual Studio

1. En el equipo de Visual Studio, abra la solución que intenta depurar (**MyASPApp** si está siguiendo los pasos de este artículo).
2. En Visual Studio, haga clic en **Depurar > Asociar al proceso** (Ctrl+Alt+P).

    > [!TIP]
    > En Visual Studio 2017 y versiones posteriores, puede volver a asociarla al mismo proceso que antes mediante **Depurar > Reasociar al proceso...** (Mayús+Alt+P).

3. Establezca el campo Calificador en **\<nombre del equipo remoto>** y presione **Entrar**.

    Compruebe que Visual Studio agrega el puerto necesario al nombre del equipo, que aparece en el formato **\<nombre del equipo remoto >:puerto**.

    ::: moniker range=">=vs-2019"
    En Visual Studio 2019, debería ver **\<nombre del equipo remoto >:4024**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    En Visual Studio 2017, debería ver **\<nombre del equipo remoto >:4022**.
    ::: moniker-end
    El puerto es obligatorio. Si no ve el número de puerto, agréguelo manualmente.

4. Haga clic en **Actualizar**.
    Debería ver que algunos procesos aparecen en la ventana **Procesos disponibles**.

    Si no ve ningún proceso, pruebe a usar la dirección IP en lugar del nombre del equipo remoto (el puerto es obligatorio). Puede usar `ipconfig` en una línea de comandos para obtener la dirección IPv4.

5. Active **Mostrar los procesos de todos los usuarios**.

6. Escriba la primera letra del nombre del proceso para encontrar rápidamente **w3wp.exe** para ASP.NET 4.5.

    Si tiene varios procesos que muestran **w3wp.exe**, compruebe la columna **Nombre de usuario**. En algunos escenarios, en la columna **Nombre de usuario** se muestra el nombre del grupo de aplicaciones, como **IIS APPPOOL\DefaultAppPool**. Si ve el grupo de aplicaciones, una manera sencilla de identificar el proceso correcto es crear uno con nombre para la instancia de la aplicación que quiera depurar y, después, lo podrá encontrar fácilmente en la columna **Nombre de usuario**.

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. Haga clic en **Adjuntar**

8. Abra el sitio web del equipo remoto. En un explorador, vaya a **http://\<nombre del equipo remoto>** .

    Debería ver la página web de ASP.NET.
9. En la aplicación de ASP.NET en ejecución, haga clic en el vínculo a la página **Acerca de**.

    Se alcanzará el punto de interrupción en Visual Studio.

## <a name="troubleshooting-open-required-ports-on-windows-server"></a><a name="bkmk_openports"></a> Solución de problemas: apertura de los puertos obligatorios en Windows Server

En la mayoría de las instalaciones, los puertos obligatorios se abren mediante la instalación de ASP.NET y el depurador remoto. Pero es posible que tenga que comprobar que los puertos están abiertos.

> [!NOTE]
> En una máquina virtual de Azure, debe abrir los puertos a través del [grupo de seguridad de red](/azure/virtual-machines/windows/nsg-quickstart-portal).

Puertos obligatorios:

* 80: obligatorio para IIS
::: moniker range=">=vs-2019"
* 4024: obligatorio para la depuración remota desde Visual Studio 2019 (vea [Asignaciones de puertos del depurador remoto](../debugger/remote-debugger-port-assignments.md) para obtener más información).
::: moniker-end
::: moniker range="vs-2017"
* 4022: obligatorio para la depuración remota desde Visual Studio 2017 (vea [Asignaciones de puertos del depurador remoto](../debugger/remote-debugger-port-assignments.md) para obtener más información).
::: moniker-end
* UDP 3702: (opcional) el puerto de detección habilita el botón **Buscar** al asociarse al depurador remoto en Visual Studio.

1. Para abrir un puerto en Windows Server, abra el menú **Inicio**, busque **Firewall de Windows con seguridad avanzada**.

2. Después, elija **Reglas de entrada > Regla nueva > Puerto**. Elija **Siguiente** y, en **Puertos locales específicos**, escriba el número de puerto, haga clic en **Siguiente** y **Permitir la conexión**. Luego, haga clic en Siguiente y agregue el nombre (**IIS**, **Web Deploy**o **msvsmon**) para la regla de entrada.

    Si quiere más información sobre cómo configurar el Firewall de Windows, vea [Configuración del Firewall de Windows para la depuración remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Cree reglas adicionales para los demás puertos obligatorios.