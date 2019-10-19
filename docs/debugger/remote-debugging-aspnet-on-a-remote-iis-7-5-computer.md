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
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/17/2019
ms.locfileid: "72536021"
---
# <a name="remote-debug-aspnet-on-a-remote-iis-computer"></a>Depuración remota de ASP.NET en un equipo remoto de IIS
Para depurar una aplicación de ASP.NET que se ha implementado en IIS, instale y ejecute las herramientas remotas en el equipo donde ha implementado la aplicación y, a continuación, conéctese a la aplicación en ejecución desde Visual Studio.

![Componentes del Depurador remoto](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

En esta guía se explica cómo instalar y configurar una aplicación de Visual Studio ASP.NET MVC 4.5.2, implementarla en IIS y adjuntar el depurador remoto desde Visual Studio.

> [!NOTE]
> Para depurar de forma remota ASP.NET Core en su lugar, vea [ASP.net Core de depuración remota en un equipo de IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md). Por Azure App Service, puede implementar y depurar fácilmente en una instancia preconfigurada de IIS mediante el [Snapshot Debugger](../debugger/debug-live-azure-applications.md) (se requiere .net 4.6.1) o [adjuntando el depurador de explorador de servidores](../debugger/remote-debugging-azure.md).

## <a name="prerequisites"></a>Requisitos previos

::: moniker range=">=vs-2019"
Visual Studio 2019 es necesario para seguir los pasos que se muestran en este artículo.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017 es necesario para seguir los pasos que se muestran en este artículo.
::: moniker-end

Estos procedimientos se han probado en estas configuraciones de servidor:
* Windows Server 2012 R2 e IIS 8 (para Windows Server 2008 R2, los pasos del servidor son diferentes)

## <a name="network-requirements"></a>Requisitos de red

El depurador remoto es compatible con Windows Server a partir de Windows Server 2008 Service Pack 2. Para obtener una lista completa de los requisitos, consulte [requisitos](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> No se admite la depuración entre dos equipos conectados a través de un proxy. No se recomienda la depuración a través de una conexión de alta latencia o de ancho de banda bajo, como acceso telefónico a Internet o a través de Internet a través de países, y puede producir un error o ser inaceptablemente lento.

## <a name="app-already-running-in-iis"></a>¿La aplicación ya se está ejecutando en IIS?

En este artículo se incluyen los pasos para configurar una configuración básica de IIS en Windows Server e implementar la aplicación desde Visual Studio. Estos pasos se incluyen para asegurarse de que el servidor tiene instalados los componentes necesarios, que la aplicación se puede ejecutar correctamente y que está listo para la depuración remota.

* Si la aplicación se ejecuta en IIS y solo desea descargar el depurador remoto e iniciar la depuración, vaya a [Descargar e instalar las herramientas remotas en Windows Server](#BKMK_msvsmon).

* Si desea obtener ayuda para asegurarse de que la aplicación está configurada, implementada y ejecutándose correctamente en IIS para que pueda depurar, siga todos los pasos de este tema.

## <a name="create-the-aspnet-452-application-on-the-visual-studio-computer"></a>Creación de la aplicación ASP.NET 4.5.2 en el equipo de Visual Studio

1. Cree una nueva aplicación de MVC ASP.NET

    ::: moniker range=">=vs-2019"
    En Visual Studio 2019, escriba **Ctrl + Q** para abrir el cuadro de búsqueda, escriba **ASP.net**, elija **plantillas**y, a continuación, elija **crear nueva aplicación Web de ASP.net (.NET Framework)** . En el cuadro de diálogo que aparece, asigne al proyecto el nombre **MyASPApp**y, a continuación, elija **crear**. Seleccione **MVC** y elija **crear**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Para hacer esto en Visual Studio 2017, elija **archivo > nuevo > proyecto**y, a continuación, seleccione **Visual C# > Web > aplicación Web ASP.net**. En la sección de plantillas **ASP.NET 4.5.2** , seleccione **MVC**. Asegúrese de que la opción **Habilitar compatibilidad con Docker** no está seleccionada y que la **autenticación** está establecida en **sin autenticación**. Asigne al proyecto el nombre **MyASPApp**.)
    ::: moniker-end

2. Abra el archivo *HomeController.CS* y establezca un punto de interrupción en el método `About()`.

## <a name="bkmk_configureIIS"></a>Instalar y configurar IIS en Windows Server

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Actualizar la configuración de seguridad del explorador en Windows Server

Si la opción Configuración de seguridad mejorada está habilitada en Internet Explorer (está habilitada de forma predeterminada), es posible que deba agregar algunos dominios como sitios de confianza para poder descargar algunos de los componentes de servidor Web. Para agregar sitios de confianza, vaya a **Opciones de Internet > seguridad > sitios de confianza > sitios**. Agregue los siguientes dominios.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

Al descargar el software, puede recibir solicitudes para conceder permiso para cargar varios scripts y recursos de sitios Web. Algunos de estos recursos no son necesarios, pero para simplificar el proceso, haga clic en **Agregar** cuando se le solicite.

## <a name="BKMK_deploy_asp_net"></a>Instalación de ASP.NET 4,5 en Windows Server

Si desea obtener información más detallada para instalar ASP.NET en IIS, consulte [iis 8,0 con ASP.NET 3,5 y ASP.NET 4,5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

1. En el panel izquierdo de Administrador del servidor, seleccione **IIS**. Haga clic con el botón derecho en el servidor y seleccione **Administrador de Internet Information Services (IIS)** .

1. Use el instalador de plataforma web (WebPI) para instalar ASP.NET 4,5 (desde el nodo de servidor en Windows Server 2012 R2, elija **obtener nuevos componentes de plataforma web** y busque ASP.net).

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg_iis_aspnet_45.png "RemoteDBG_IIS_AspNet_45")

    > [!NOTE]
    > Si usa Windows Server 2008 R2, instale ASP.NET 4 en su lugar con este comando:

     **C:\Windows\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -ir**

2. Reinicie el sistema (o ejecute **net stop was /y** seguido de **net start w3svc** desde un símbolo del sistema para obtener un cambio en la ruta de acceso del sistema).

## <a name="choose-a-deployment-option"></a>Elección de una opción de implementación

Si necesita ayuda para implementar la aplicación en IIS, tenga en cuenta estas opciones:

* Para implementar, cree un archivo de configuración de publicación en IIS e importe la configuración en Visual Studio. En algunos escenarios, se trata de una manera rápida de implementar la aplicación. Al crear el archivo de configuración de publicación, los permisos se configuran automáticamente en IIS.

* Implemente la publicación en una carpeta local y copie la salida mediante un método preferido en una carpeta de aplicación preparada en IIS.

## <a name="optional-deploy-using-a-publish-settings-file"></a>Opta Implementación mediante un archivo de configuración de publicación

Puede usar esta opción para crear un archivo de configuración de publicación e importarlo en Visual Studio.

> [!NOTE]
> Este método de implementación usa Web Deploy. Si desea configurar Web Deploy manualmente en Visual Studio en lugar de importar la configuración, puede instalar Web Deploy 3,6 en lugar de Web Deploy 3,6 para los servidores de hospedaje. Sin embargo, si configura Web Deploy manualmente, deberá asegurarse de que una carpeta de aplicación del servidor está configurada con los valores y permisos correctos (vea [configurar el sitio web de ASP.net](#BKMK_deploy_asp_net)).

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Instalación y configuración de Web Deploy para hospedar servidores en Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Crear el archivo de configuración de publicación en IIS en Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importar la configuración de publicación a Visual Studio e implementar

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Después de que se implemente la aplicación correctamente, debería iniciarse automáticamente. Si la aplicación no se inicia desde Visual Studio, inicie la aplicación en IIS.

1. En el cuadro de diálogo **configuración** , habilite la depuración; para ello, haga clic en **siguiente**, elija una configuración de **depuración** y, a continuación, elija **quitar archivos adicionales en destino** en opciones de **publicación de archivos** .

    > [!NOTE]
    > Si elige una configuración de versión, deshabilite la depuración en el archivo *Web. config* al publicar.

1. Haga clic en **Guardar** y, a continuación, vuelva a publicar la aplicación.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>Opta Implementación mediante la publicación en una carpeta local

Puede usar esta opción para implementar la aplicación si quiere copiar la aplicación en IIS con PowerShell, RoboCopy o desea copiar manualmente los archivos.

### <a name="BKMK_deploy_asp_net"></a>Configurar el sitio web de ASP.NET en el equipo de Windows Server

1. Abra el explorador de Windows y cree una nueva carpeta, **C:\Publish**, donde implementará más adelante el proyecto ASP.net.

2. Si aún no está abierto, abra el **Administrador de Internet Information Services (IIS)** . (En el panel izquierdo de Administrador del servidor, seleccione **IIS**. Haga clic con el botón derecho en el servidor y seleccione **Administrador de Internet Information Services (IIS)** .)

3. En **conexiones** en el panel izquierdo, vaya a **sitios**.

4. Seleccione el **sitio web predeterminado**, elija **configuración básica**y establezca la **ruta de acceso física** en **C:\Publish**.

5. Haga clic con el botón secundario en el nodo **Sitio web predeterminado** y seleccione **Agregar aplicación**.

6. Establezca el campo **alias** en **MyASPApp**, acepte el grupo de aplicaciones predeterminado (**DefaultAppPool**) y establezca la **ruta de acceso física** en **C:\Publish**.

7. En **conexiones**, seleccione **grupos de aplicaciones**. Abra **DefaultAppPool** y establezca el campo Grupo de aplicaciones en **ASP.net v 4.0** (ASP.net 4,5 no es una opción para el grupo de aplicaciones).

8. Con el sitio seleccionado en el administrador de IIS, elija **Editar permisos**y asegúrese de que IUSR, IIS_IUSRS o el usuario configurado para el grupo de aplicaciones sea un usuario autorizado con derechos de lectura & ejecución. Si ninguno de estos usuarios está presente, agregue IUSR como usuario con derechos de lectura & ejecución.

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Publicar e implementar la aplicación mediante la publicación en una carpeta local desde Visual Studio

También puede publicar e implementar la aplicación con el sistema de archivos u otras herramientas.

1. (ASP.NET 4.5.2) Asegúrese de que el archivo Web. config muestra la versión correcta de .NET.  Por ejemplo, si tiene como destino ASP.NET 4.5.2, asegúrese de que esta versión aparece en Web. config.

    ```xml
    <system.web>
      <compilation debug="true" targetFramework="4.5.2" />
      <httpRuntime targetFramework="4.5.2" />
      <httpModules>
        <add name="ApplicationInsightsWebTracking" type="Microsoft.ApplicationInsights.Web.ApplicationInsightsHttpModule, Microsoft.AI.Web" />
      </httpModules>
    </system.web>

    ```

    Por ejemplo, la versión debe ser 4,0 si instala ASP.NET 4 en lugar de 4.5.2.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="BKMK_msvsmon"></a>Descargar e instalar las herramientas remotas en Windows Server

Descargue la versión de las herramientas remotas que coincida con su versión de Visual Studio.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="BKMK_setup"></a> Establecimiento del depurador remoto en Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Si necesita agregar permisos para usuarios adicionales, cambie el modo de autenticación o el número de puerto para el depurador remoto, vea [configurar el depurador remoto](../debugger/remote-debugging.md#configure_msvsmon).

Para obtener información sobre cómo ejecutar el depurador remoto como servicio, vea [ejecutar el depurador remoto como servicio](../debugger/remote-debugging.md#bkmk_configureService).

## <a name="BKMK_attach"></a> Adjuntar elementos a la aplicación ASP.NET desde el equipo de Visual Studio

1. En el equipo de Visual Studio, abra la solución que está intentando depurar (**MyASPApp** si está siguiendo los pasos descritos en este artículo).
2. En Visual Studio, haga clic en **Depurar > asociar al proceso** (Ctrl + Alt + P).

    > [!TIP]
    > En Visual Studio 2017 y versiones posteriores, puede volver a asociar al mismo proceso que adjuntó anteriormente a mediante **Debug > volver a adjuntar al proceso...** (Mayús + Alt + P).

3. Establezca el campo calificador en **\<remote nombre de equipo >** y presione **entrar**.

    Compruebe que Visual Studio agrega el puerto necesario al nombre del equipo, que aparece en el formato: **\<remote nombre de equipo >:p ordenar**

    ::: moniker range=">=vs-2019"
    En Visual Studio 2019, debería ver **\<remote nombre de equipo >: 4024**
    ::: moniker-end
    ::: moniker range="vs-2017"
    En Visual Studio 2017, debería ver **\<remote nombre de equipo >: 4022**
    ::: moniker-end
    El puerto es obligatorio. Si no ve el número de puerto, agréguelo manualmente.

4. Haga clic en **Actualizar**.
    Debería ver que algunos procesos aparecen en la ventana **Procesos disponibles** .

    Si no ve ningún proceso, pruebe a usar la dirección IP en lugar del nombre del equipo remoto (el puerto es obligatorio). Puede usar `ipconfig` en una línea de comandos para obtener la dirección IPv4.

5. Active  **Mostrar los procesos de todos los usuarios**.

6. Escriba la primera letra de un nombre de proceso para encontrar rápidamente **w3wp. exe** para ASP.net 4,5.

    Si tiene varios procesos que muestran **w3wp. exe**, Compruebe la columna **nombre de usuario** . En algunos escenarios, la columna **nombre de usuario** muestra el nombre del grupo de aplicaciones, como **IIS APPPOOL\DefaultAppPool**. Si ve el grupo de aplicaciones, una manera fácil de identificar el proceso correcto es crear un nuevo grupo de aplicaciones con nombre para la instancia de la aplicación que desea depurar y, a continuación, puede encontrarlo fácilmente en la columna **nombre de usuario** .

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. Haga clic en **Adjuntar**

8. Abra el sitio web del equipo remoto. En un explorador, vaya a **http://\<nombre del equipo remoto>** .

    Debería ver la página web de ASP.NET.
9. En la aplicación ASP.NET en ejecución, haga clic en el vínculo a la página **About** .

    Se alcanzará el punto de interrupción en Visual Studio.

## <a name="bkmk_openports"></a> Solución de problemas Abra los puertos necesarios en Windows Server

En la mayoría de las instalaciones, los puertos necesarios se abren mediante la instalación de ASP.NET y el depurador remoto. Sin embargo, puede que tenga que comprobar que los puertos están abiertos.

> [!NOTE]
> En una máquina virtual de Azure, debe abrir los puertos a través del [grupo de seguridad de red](/azure/virtual-machines/windows/nsg-quickstart-portal).

Puertos necesarios:

* 80: necesario para IIS
::: moniker range=">=vs-2019"
* 4024: necesario para la depuración remota desde Visual Studio 2019 (vea [asignaciones de puerto del Depurador remoto](../debugger/remote-debugger-port-assignments.md) para obtener más información).
::: moniker-end
::: moniker range="vs-2017"
* 4022: necesario para la depuración remota desde Visual Studio 2017 (vea [asignaciones de puerto del Depurador remoto](../debugger/remote-debugger-port-assignments.md) para obtener más información).
::: moniker-end
* UDP 3702: (opcional) el puerto de detección permite el botón **Buscar** al asociarse al depurador remoto en Visual Studio.

1. Para abrir un puerto en Windows Server, abra el menú **Inicio** , busque **firewall de Windows con seguridad avanzada**.

2. A continuación, elija **reglas de entrada > nueva regla > puerto**. Elija **siguiente** y, en **puertos locales específicos**, escriba el número de puerto, haga clic en **siguiente**y, a continuación, **permita la conexión**, haga clic en siguiente y agregue el nombre (**IIS**, **Web deploy**o **msvsmon**) para la regla de entrada.

    Si desea obtener más información acerca de cómo configurar el Firewall de Windows, consulte [configurar Firewall de Windows para la depuración remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Cree reglas adicionales para los demás puertos necesarios.