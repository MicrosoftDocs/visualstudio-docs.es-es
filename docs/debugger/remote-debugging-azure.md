---
title: Depurar ASP.NET núcleo remoto en IIS y Azure Microsoft Docs
ms.custom: remotedebugging
ms.date: 04/14/2020
ms.topic: conceptual
ms.assetid: a6c04b53-d1b9-4552-a8fd-3ed6f4902ce6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
- dotnetcore
- azure
ms.openlocfilehash: 079e324f2304118c9041118c13e8ebc0cce2015c
ms.sourcegitcommit: cc58ca7ceae783b972ca25af69f17c9f92a29fc2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/15/2020
ms.locfileid: "81385507"
---
# <a name="remote-debug-aspnet-core-on-iis-in-azure-in-visual-studio"></a>Depuración remota ASP.NET Core en IIS en Azure en Visual Studio

En esta guía se explica cómo configurar y configurar una aplicación de Visual Studio ASP.NET Core, implementarla en IIS mediante Azure y adjuntar el depurador remoto desde Visual Studio.

La forma recomendada de depurar remotamente en Azure depende de su escenario:

* Para depurar ASP.NET Core en Azure App Service, consulte Depurar aplicaciones de Azure mediante el depurador de [instantáneas](../debugger/debug-live-azure-applications.md). Éste es el método recomendado.
* Para depurar ASP.NET Core en Azure App Service con características de depuración más tradicionales, siga los pasos de este tema (consulte la sección [Depuración remota en Azure App Service](#remote_debug_azure_app_service)).

    En este escenario, debe implementar la aplicación desde Visual Studio a Azure, pero no es necesario instalar o configurar manualmente IIS o el depurador remoto (estos componentes se representan con líneas de puntos), como se muestra en la siguiente ilustración.

    ![Componentes del depurador remoto](../debugger/media/remote-debugger-azure-app-service.png "Remote_debugger_components")

* Para depurar IIS en una máquina virtual de Azure, siga los pasos de este tema (consulte la sección [Depuración remota en una máquina virtual](#remote_debug_azure_vm)de Azure). Esto le permite usar una configuración personalizada de IIS, pero los pasos de configuración e implementación son más complicados.

    Para una máquina virtual de Azure, debe implementar la aplicación desde Visual Studio en Azure y también debe instalar manualmente el rol IIS y el depurador remoto, como se muestra en la siguiente ilustración.

    ![Componentes del depurador remoto](../debugger/media/remote-debugger-azure-vm.png "Remote_debugger_components")

* Para depurar ASP.NET Core en Azure Service Fabric, vea [Depurar una aplicación remota](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)de Service Fabric .

> [!WARNING]
> Asegúrese de eliminar los recursos de Azure que cree cuando haya completado los pasos de este tutorial. De esa manera puede evitar incurrir en cargos innecesarios.

## <a name="prerequisites"></a>Prerrequisitos

::: moniker range=">=vs-2019"
Visual Studio 2019 es necesario seguir los pasos que se muestran en este artículo.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017 es necesario seguir los pasos que se muestran en este artículo.
::: moniker-end

### <a name="network-requirements"></a>Requisitos de red

No se admite la depuración entre dos equipos conectados a través de un proxy. No se recomienda depurar a través de una conexión de alta latencia o bajo ancho de banda, como Internet de acceso telefónico o a través de Internet entre países, y puede fallar o ser inaceptablemente lento. Para obtener una lista completa de los requisitos, consulte [Requisitos](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Cree la aplicación ASP.NET Core en el equipo de Visual Studio

1. Cree una nueva aplicación ASP.NET Core.

    ::: moniker range=">=vs-2019"
    En Visual Studio 2019, escriba **Ctrl + Q** para abrir el cuadro de búsqueda, escriba **asp.net**, elija **Plantillas**y, a continuación, elija Crear nueva aplicación web **ASP.NET principal**. En el cuadro de diálogo que aparece, asigne al proyecto el nombre **MyASPApp**y, a continuación, elija **Create .** A continuación, elija **Web Application (Model-View-Controller)** y, a continuación, elija **Create**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    En Visual Studio 2017, elija **Archivo > Nuevo > proyecto**y, a continuación, seleccione Visual **C-> Web > ASP.NET aplicación web principal**. En la sección Plantillas ASP.NET Core, seleccione **Aplicación web (Model-View-Controller).** Asegúrese de que ASP.NET Core 2.1 está seleccionado, que **Habilitar compatibilidad con Docker** no está seleccionada y que **Autenticación** está establecida en **Sin autenticación**. Asigne al proyecto el nombre **MyASPApp**.
    ::: moniker-end

1. Abra el archivo About.cshtml.cs y establezca `OnGet` un punto de interrupción en el método `About()` (en plantillas anteriores, abra HomeController.cs en su lugar y establezca el punto de interrupción en el método).

## <a name="remote-debug-aspnet-core-on-an-azure-app-service"></a><a name="remote_debug_azure_app_service"></a>Depuración remota ASP.NET núcleo en un servicio de aplicaciones de Azure

Desde Visual Studio, puede publicar y depurar rápidamente la aplicación en una instancia totalmente aprovisionada de IIS. Sin embargo, la configuración de IIS está preestablecida y no se puede personalizar. Para obtener instrucciones más detalladas, vea [Implementar una aplicación web ASP.NET Core](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)en Azure mediante Visual Studio . (Si necesita la capacidad de personalizar IIS, intente depurar en una [máquina virtual](#remote_debug_azure_vm)de Azure .)

#### <a name="to-deploy-the-app-and-remote-debug-using-cloud-explorer"></a>Para implementar la aplicación y la depuración remota mediante Cloud Explorer

1. En Visual Studio, haga clic con el botón secundario en el nodo del proyecto y elija **Publicar**.

    Si previamente ha configurado algún perfil de publicación, aparece el panel **Publicar**. Haga clic en **Nuevo perfil**.

1. Elija **Azure App Service** en el cuadro de diálogo **Publicar,** seleccione **Crear nuevo**y siga las indicaciones para crear un perfil.

    Para obtener instrucciones detalladas, vea [Publicar una aplicación de ASP.NET Core en Azure con Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

    ![Publicar en Azure App Service](../debugger/media/remotedbg_azure_app_service_profile.png)

1. En la ventana Publicar, elija **Editar configuración** y cambie a una configuración de depuración y, a continuación, elija **Publicar**.

   Se requiere una configuración de depuración para depurar la aplicación.

1. Abra **Cloud Explorer** (**View** > Cloud**Explorer**), haga clic con el botón derecho en la instancia de App Service y elija Attach **Debugger**.

   Si Cloud Explorer no está disponible, abra el Explorador de servidores en su lugar. A continuación, haga clic con el botón derecho en la instancia de App Service en el Explorador de servidores y elija **Attach Debugger**.

1. En la aplicación ASP.NET en ejecución, haga clic en el vínculo a la página **Acerca de.**

    Se alcanzará el punto de interrupción en Visual Studio.

    Eso es todo. El resto de los pasos de este tema se aplican a la depuración remota en una máquina virtual de Azure.The rest area of the steps in this topic se aplican a la depuración remota en una máquina virtual de Azure.The rest area of the steps in this topic se

## <a name="remote-debug-aspnet-core-on-an-azure-vm"></a><a name="remote_debug_azure_vm"></a>Central de depuración remota ASP.NET en una máquina virtual de Azure

Puede crear una máquina virtual de Azure para Windows Server y, a continuación, instalar y configurar IIS y los demás componentes de software necesarios. Esto lleva más tiempo que la implementación en azure App Service y requiere que siga los pasos restantes de este tutorial.

Estos procedimientos se han probado en estas configuraciones del servidor:
* Windows Server 2012 R2 e IIS 8
* Windows Server 2016 e IIS 10

### <a name="app-already-running-in-iis-on-the-azure-vm"></a>¿La aplicación ya se está ejecutando en IIS en la máquina virtual de Azure?

En este artículo se incluyen los pasos para configurar una configuración básica de IIS en el servidor de Windows e implementar la aplicación desde Visual Studio. Estos pasos se incluyen para asegurarse de que el servidor tiene instalados los componentes necesarios, que la aplicación se puede ejecutar correctamente y que está listo para depurar de forma remota.

* Si la aplicación se ejecuta en IIS y solo desea descargar el depurador remoto e iniciar la depuración, vaya a [Descargar e instalar las herramientas remotas en Windows Server](#BKMK_msvsmon).

* Si desea ayuda para asegurarse de que la aplicación está configurada, implementada y ejecutándose correctamente en IIS para que pueda depurar, siga todos los pasos de este tema.

  * Antes de comenzar, siga todos los pasos descritos en [Instalar y ejecutar IIS](/azure/virtual-machines/windows/quick-create-portal).

  * Cuando abra el puerto 80 en el grupo de seguridad de red, abra también el [puerto correcto](#bkmk_openports) para el depurador remoto (4024 o 4022). De esa manera, no tendrás que abrirlo más tarde.

### <a name="update-browser-security-settings-on-windows-server"></a>Actualizar la configuración de seguridad del explorador en Windows Server

Si la configuración de seguridad mejorada está habilitada en Internet Explorer (está habilitada de forma predeterminada), es posible que deba agregar algunos dominios como sitios de confianza para permitirle descargar algunos de los componentes del servidor web. Agregue los sitios de confianza yendo a Opciones de **Internet > Seguridad > Sitios de > de confianza**. Agregue los siguientes dominios.

- microsoft.com
- go.microsoft.com
- download.Microsoft.com
- iis.net

Al descargar el software, puede obtener solicitudes para conceder permiso para cargar varios scripts y recursos de sitios web. Algunos de estos recursos no son necesarios, pero para simplificar el proceso, haga clic en **Agregar** cuando se le solicite.

### <a name="install-aspnet-core-on-windows-server"></a>Instalar ASP.NET Core en Windows Server

1. Instale el [lote de hospedaje .NET Core Windows Server](https://aka.ms/dotnetcore-2-windowshosting) en el sistema host. El lote instala .NET Core Runtime, .NET Core Library y el módulo ASP.NET Core. Para obtener instrucciones más detalladas, consulte Publicación en [IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    > [!NOTE]
    > Si el sistema no tiene conexión a Internet, obtenga e instale *[Microsoft Visual C++ 2015 Redistributable](https://www.microsoft.com/download/details.aspx?id=53840)* antes de instalar el lote de hospedaje .NET Core Windows Server.

3. Reinicie el sistema (o ejecute **net stop was /y** seguido de **net start w3svc** desde un símbolo del sistema para obtener un cambio en la ruta de acceso del sistema).

## <a name="choose-a-deployment-option"></a>Elija una opción de implementación

Si necesita ayuda para implementar la aplicación en IIS, tenga en cuenta estas opciones:

* Implementar mediante la creación de un archivo de configuración de publicación en IIS e importar la configuración en Visual Studio. En algunos escenarios, esta es una forma rápida de implementar la aplicación. Al crear el archivo de configuración de publicación, los permisos se configuran automáticamente en IIS.

* Implementar mediante la publicación en una carpeta local y copiar la salida por un método preferido en una carpeta de aplicación preparada en IIS.

## <a name="optional-deploy-using-a-publish-settings-file"></a>(Opcional) Implementar mediante un archivo de configuración de publicación

Puede usar esta opción para crear un archivo de configuración de publicación e importarlo en Visual Studio.

> [!NOTE]
> Este método de implementación usa Web Deploy. Si desea configurar Web Deploy manualmente en Visual Studio en lugar de importar la configuración, puede instalar Web Deploy 3.6 en lugar de Web Deploy 3.6 para servidores de hospedaje. Sin embargo, si configura Web Deploy manualmente, deberá asegurarse de que una carpeta de aplicación en el servidor está configurada con los valores y permisos correctos (consulte [Configurar ASP.NET sitio web).](#BKMK_deploy_asp_net)

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Instalar y configurar Web Deploy para servidores de hospedaje en Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Crear el archivo de configuración de publicación en IIS en Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importar la configuración de publicación a Visual Studio e implementar

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Después de que se implemente la aplicación correctamente, debería iniciarse automáticamente. Si la aplicación no se inicia desde Visual Studio, inicie la aplicación en IIS. Para ASP.NET Core, deberá asegurarse de que el campo Grupo de aplicaciones para el **DefaultAppPool** está establecido en **Sin código administrado**.

1. En el cuadro de diálogo **Configuración,** habilite la depuración haciendo clic en **Siguiente**, elija una configuración de **depuración** y, a continuación, elija **Quitar archivos adicionales en destino** en las opciones de **publicación** de archivos.

    > [!NOTE]
    > Si elige una configuración de versión, deshabilite la depuración en el archivo *web.config* al publicar.

1. Haga clic en **Guardar** y, a continuación, vuelva a publicar la aplicación.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(Opcional) Implementar mediante la publicación en una carpeta local

Puede usar esta opción para implementar la aplicación si desea copiar la aplicación en IIS mediante PowerShell, RoboCopy o si desea copiar manualmente los archivos.

### <a name="configure-the-aspnet-core-web-site-on-the-windows-server-computer"></a><a name="BKMK_deploy_asp_net"></a>Configurar el sitio Web ASP.NET Core en el equipo con Windows Server

Si va a importar la configuración de publicación, puede omitir esta sección.

1. Abra el **Administrador de Internet Information Services (IIS)** y vaya a **Sitios**.

2. Haga clic con el botón secundario en el nodo **Sitio web predeterminado** y seleccione **Agregar aplicación**.

3. Establezca el campo **Alias** en **MyASPApp** y el campo Grupo de aplicaciones en **Sin código administrado**. Establezca la ruta de **acceso física** en **C:-Publicar** (donde más adelante implementará el proyecto ASP.NET Core).

4. Con el sitio seleccionado en el Administrador de IIS, elija **Editar permisos**y asegúrese de que IUSR, IIS_IUSRS o el usuario configurado para el grupo de aplicaciones es un usuario autorizado con derechos de lectura & ejecutar.

    Si no ve uno de estos usuarios con acceso, siga los pasos para agregar IUSR como usuario con derechos de & Ejecutar.

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>(Opcional) Publicar e implementar la aplicación mediante la publicación en una carpeta local desde Visual Studio

Si no usa Web Deploy, debe publicar e implementar la aplicación mediante el sistema de archivos u otras herramientas. Puede empezar creando un paquete mediante el sistema de archivos y, a continuación, implementar el paquete manualmente o usar otras herramientas como PowerShell, RoboCopy o XCopy. En esta sección, suponemos que está copiando manualmente el paquete si no está utilizando Web Deploy.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="download-and-install-the-remote-tools-on-windows-server"></a><a name="BKMK_msvsmon"></a>Descargar e instalar las herramientas remotas en Windows Server

Descargue la versión de las herramientas remotas que coincida con su versión de Visual Studio.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="set-up-the-remote-debugger-on-windows-server"></a><a name="BKMK_setup"></a> Establecimiento del depurador remoto en Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Si necesita agregar permisos para usuarios adicionales, cambiar el modo de autenticación o el número de puerto para el depurador remoto, consulte [Configurar el depurador remoto](../debugger/remote-debugging.md#configure_msvsmon).

### <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a><a name="BKMK_attach"></a>Adjuntar a la aplicación ASP.NET desde el equipo de Visual Studio

1. En el equipo de Visual Studio, abra la solución que está intentando depurar (**MyASPApp** si está siguiendo los pasos de este artículo).
2. En Visual Studio, haga clic en **Depurar > Adjuntar al proceso** (Ctrl + Alt + P).

    > [!TIP]
    > En Visual Studio 2017 y versiones posteriores, puede volver a adjuntar al mismo proceso al que se asentó anteriormente mediante **Depurar > Volver a adjuntar a proceso...** (Mayús+Alt+P).

3. Establezca el campo Calificador en nombre de ** \<equipo remoto>** y pulse **Intro**.

    Compruebe que Visual Studio agrega el puerto necesario al nombre del equipo, que aparece en el formato: ** \<nombre de equipo remoto>:port**

    ::: moniker range=">=vs-2019"
    En Visual Studio 2019, debería ver ** \<el nombre de equipo remoto>:4024**
    ::: moniker-end
    ::: moniker range="vs-2017"
    En Visual Studio 2017, debería ver ** \<el nombre del equipo remoto>:4022**
    ::: moniker-end
    El puerto es necesario. Si no ve el número de puerto, agréguelo manualmente.

4. Haga clic en **Actualizar**.
    Debería ver que algunos procesos aparecen en la ventana **Procesos disponibles** .

    Si no ve ningún proceso, intente usar la dirección IP en lugar del nombre del equipo remoto (el puerto es necesario). Puede utilizar `ipconfig` en una línea de comandos para obtener la dirección IPv4.

    Si desea utilizar el botón **Buscar,** es posible que deba abrir el [puerto UDP 3702](#bkmk_openports) en el servidor.

5. Active  **Mostrar los procesos de todos los usuarios**.

6. Escriba la primera letra del nombre del proceso para encontrar rápidamente la aplicación.

    * Seleccionar **dotnet.exe** (para .NET Core)

      Si tiene varios procesos que muestran **dotnet.exe**, compruebe la columna **Nombre de usuario.** En algunos escenarios, la columna **Nombre** de usuario muestra el nombre del grupo de aplicaciones, como **IIS APPPOOL-DefaultAppPool**. Si ve el grupo de aplicaciones, una manera fácil de identificar el proceso correcto es crear un nuevo grupo de aplicaciones con nombre para la instancia de aplicación que desea depurar y, a continuación, puede encontrarlo fácilmente en la columna **Nombre** de usuario.

    * En algunos escenarios de IIS, puede encontrar el nombre de la aplicación en la lista de procesos, como **MyASPApp.exe**. Puede adjuntar a este proceso en su lugar.

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. Haga clic en **Asociar**.

8. Abra el sitio web del equipo remoto. En un explorador, vaya a **http://\<nombre del equipo remoto>**.

    Debería ver la página web de ASP.NET.
9. En la aplicación ASP.NET en ejecución, haga clic en el vínculo a la página **Acerca de.**

    Se alcanzará el punto de interrupción en Visual Studio.

### <a name="troubleshooting-open-required-ports-on-windows-server"></a><a name="bkmk_openports"></a> Solución de problemas Abra los puertos necesarios en Windows Server

En la mayoría de las configuraciones, los puertos necesarios se abren mediante la instalación de ASP.NET y el depurador remoto. Sin embargo, si está solucionando problemas de implementación y la aplicación está hospedada detrás de un firewall, es posible que deba comprobar que los puertos correctos están abiertos.

En una máquina virtual de Azure, debe abrir puertos a través del [grupo de seguridad](/azure/virtual-machines/windows/nsg-quickstart-portal)de red .

Puertos requeridos:

* 80 - Requerido para IIS
::: moniker range=">=vs-2019"
* 4024 - Necesario para la depuración remota desde Visual Studio 2019 (consulte [Asignaciones](../debugger/remote-debugger-port-assignments.md) de puertos del depurador remoto para obtener más información).
::: moniker-end
::: moniker range="vs-2017"
* 4022 - Necesario para la depuración remota desde Visual Studio 2017 (consulte [Asignaciones](../debugger/remote-debugger-port-assignments.md) de puertos del depurador remoto para obtener más información).
::: moniker-end
* UDP 3702 - (Opcional) puerto de detección le permite el botón **Buscar** al asociar al depurador remoto en Visual Studio.

Además, estos puertos ya deben ser abiertos por la instalación ASP.NET:
- 8172 - (Opcional) Requerido para que Web Deploy implemente la aplicación desde Visual Studio
