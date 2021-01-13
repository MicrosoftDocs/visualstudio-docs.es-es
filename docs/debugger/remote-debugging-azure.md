---
title: Depuración remota de ASP.NET Core en IIS y Azure | Microsoft Docs
description: Obtenga información sobre cómo configurar una aplicación de ASP.NET Core en Visual Studio, implementarla en IIS con Azure y agregar el depurador remoto de Visual Studio.
ms.custom: remotedebugging
ms.date: 05/06/2020
ms.topic: conceptual
ms.assetid: a6c04b53-d1b9-4552-a8fd-3ed6f4902ce6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
- dotnetcore
- azure
ms.openlocfilehash: b6535bb52221de780b9a8862be22a6a4deb79b57
ms.sourcegitcommit: 105e7b5a486262bc92939980383ceee068098a11
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/30/2020
ms.locfileid: "97815846"
---
# <a name="remote-debug-aspnet-core-on-iis-in-azure-in-visual-studio"></a>Depuración remota de ASP.NET Core en IIS en Azure en Visual Studio

En esta guía se explica cómo configurar una aplicación ASP.NET Core en Visual Studio, implementarla en IIS con Azure y agregar el depurador remoto de Visual Studio.

El método recomendado para la depuración remota en Azure dependerá de su escenario:

* Para depurar ASP.NET Core en Azure App Service, vea [Depuración de aplicaciones de Azure con Snapshot Debugger](../debugger/debug-live-azure-applications.md). Éste es el método recomendado.
* Para depurar ASP.NET Core en Azure App Service usando características de depuración más tradicionales, siga los pasos de este tema (vea la sección [Depuración remota en Azure App Service](#remote_debug_azure_app_service)).

    En este escenario debe implementar la aplicación desde Visual Studio en Azure, pero no es necesario instalar ni configurar manualmente IIS o el depurador remoto (estos componentes se representan con líneas de puntos), tal y como se muestra en la siguiente ilustración.

    ![Diagrama en el que se muestra la relación entre Visual Studio, Azure App Service y una aplicación de ASP.NET. IIS y el depurador remoto están representados con líneas de puntos.](../debugger/media/remote-debugger-azure-app-service.png)

* Para depurar IIS en una máquina virtual de Azure, siga los pasos de este tema (vea la sección [Depuración remota en una máquina virtual de Azure](#remote_debug_azure_vm)). Esto le permite usar una configuración personalizada de IIS, pero los pasos de instalación e implementación son más complicados.

    En el caso de una máquina virtual de Azure, debe implementar la aplicación desde Visual Studio en Azure, así como instalar manualmente el rol de IIS y el depurador remoto, tal y como se muestra en la siguiente ilustración.

    ![Diagrama en el que se muestra la relación entre Visual Studio, una máquina virtual de Azure y una aplicación de ASP.NET. IIS y el depurador remoto están representados con líneas sólidas.](../debugger/media/remote-debugger-azure-vm.png)

* Para depurar ASP.NET Core en Azure Service Fabric, vea [Depurar una aplicación de Service Fabric remota](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application).

> [!WARNING]
> Asegúrese de eliminar los recursos de Azure que cree cuando haya acabado los pasos de este tutorial. De este modo, puede evitar incurrir en cargos innecesarios.

## <a name="prerequisites"></a>Requisitos previos

::: moniker range=">=vs-2019"
Para seguir los pasos que se muestran en este artículo, se requiere Visual Studio 2019.
::: moniker-end
::: moniker range="vs-2017"
Se necesita Visual Studio 2017 para seguir los pasos que se muestran en este artículo.
::: moniker-end

### <a name="network-requirements"></a>Requisitos de red

No se admite la depuración entre dos equipos conectados a través de un proxy. No se recomienda la depuración a través de una conexión de latencia alta o de ancho de banda bajo, como Internet mediante acceso telefónico o Internet a través de países, y puede producir un error o ser inaceptablemente lenta. Para obtener una lista completa de los requisitos, vea [Requisitos](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Creación de la aplicación de ASP.NET Core en el equipo de Visual Studio

1. Cree una aplicación de ASP.NET Core.

    ::: moniker range=">=vs-2019"
    En Visual Studio 2019, presione **Ctrl + Q** para abrir el cuadro de búsqueda, escriba **asp.net**, elija **Plantillas** y luego, **Crear una aplicación web ASP.NET Core**. En el cuadro de diálogo que se muestra, asigne el nombre **MyASPApp** al proyecto y después elija **Crear**. Después, elija **Aplicación web (Modelo-Vista-Controlador)** y luego **Crear**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    En Visual Studio 2017, seleccione **Archivo > Nuevo > Proyecto** y después **Visual C# > Web > Aplicación web ASP.NET Core**. En la sección Plantillas de ASP.NET Core, seleccione **Aplicación web (Modelo-Vista-Controlador)** . Asegúrese de que se ha seleccionado ASP.NET Core 2.1, que **Habilitar compatibilidad con Docker** no está seleccionado y que la opción **Autenticación** está establecida en **Sin autenticación**. Asigne el nombre **MyASPApp** al proyecto.
    ::: moniker-end

1. Abra el archivo About.cshtml.cs y establezca un punto de interrupción en el método `OnGet` (en plantillas anteriores, abra HomeController.cs en su lugar y establezca el punto de interrupción en el método `About()`).

## <a name="remote-debug-aspnet-core-on-an-azure-app-service"></a><a name="remote_debug_azure_app_service"></a> Depuración remota de ASP.NET Core en Azure App Service

Desde Visual Studio puede publicar y depurar rápidamente la aplicación en una instancia totalmente aprovisionada de IIS. Sin embargo, la configuración de IIS está preestablecida y no se puede personalizar. Para obtener instrucciones más detalladas, vea [Publicar una aplicación de ASP.NET Core en Azure con Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs) (si necesita la capacidad de personalizar IIS, intente efectuar la depuración en una [máquina virtual de Azure](#remote_debug_azure_vm)).

#### <a name="to-deploy-the-app-and-remote-debug-using-cloud-explorer"></a>Para implementar la aplicación y la depuración remota con Cloud Explorer

1. En Visual Studio, haga clic con el botón derecho en el nodo del proyecto y elija **Publicar**.

    Si previamente ha configurado algún perfil de publicación, aparece el panel **Publicar**. Haga clic en **Nuevo perfil**.

1. Elija **Azure App Service** en el cuadro de diálogo **Publicar**, seleccione **Crear nuevo** y siga las indicaciones para crear un perfil.

    Para obtener instrucciones detalladas, vea [Publicar una aplicación de ASP.NET Core en Azure con Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

    ![Publicación en Azure App Service](../debugger/media/remotedbg_azure_app_service_profile.png)

1. En la ventana Publicar, elija **Editar configuración** y cambie a una configuración de depuración; a continuación, elija **Publicar**.

   Se necesita una configuración de depuración para depurar la aplicación.

1. Abra **Cloud Explorer** (**Ver** > **Cloud Explorer**), haga clic con el botón derecho en la instancia de App Service y elija **Asociar depurador**.

   Si Cloud Explorer no está disponible, abra el Explorador de servidores. A continuación, haga clic con el botón derecho en la instancia de App Service en el Explorador de servidores y elija **Asociar depurador**.

1. En la aplicación ASP.NET en ejecución, haga clic en el vínculo a la página **Acerca de**.

    Se alcanzará el punto de interrupción en Visual Studio.

    Ya está. El resto de los pasos de este tema se aplican a la depuración remota en una máquina virtual de Azure.

## <a name="remote-debug-aspnet-core-on-an-azure-vm"></a><a name="remote_debug_azure_vm"></a> Depuración remota de ASP.NET Core en una máquina virtual de Azure

Puede crear una máquina virtual de Azure para Windows Server y, a continuación, instalar y configurar IIS y los demás componentes de software necesarios. Esto supone más tiempo que la implementación en Azure App Service e implica seguir los pasos restantes de este tutorial.

Estos procedimientos se han probado en estas configuraciones de servidor:
* Windows Server 2012 R2 e IIS 8
* Windows Server 2016 e IIS 10
* Windows Server 2019 e IIS 10

### <a name="app-already-running-in-iis-on-the-azure-vm"></a>¿La aplicación ya se está ejecutando en IIS en la máquina virtual de Azure?

En este artículo se incluyen los pasos para realizar una configuración básica de IIS en Windows Server e implementar la aplicación desde Visual Studio. Estos pasos se incluyen para asegurarse de que el servidor tiene instalados los componentes necesarios, que la aplicación se puede ejecutar correctamente y que está listo para la depuración remota.

* Si la aplicación se ejecuta en IIS y solo desea descargar el depurador remoto e iniciar la depuración, vaya a [Descarga e instalación de las herramientas remotas en Windows Server](#BKMK_msvsmon).

* Si desea obtener ayuda para asegurarse de que la aplicación está configurada, implementada y se ejecuta correctamente en IIS para poder realizar la depuración, siga todos los pasos de este tema.

  * Antes de comenzar, siga todos los pasos que se describen en [Instalación y ejecución de IIS](/azure/virtual-machines/windows/quick-create-portal).

  * Al abrir el puerto 80 en el grupo de seguridad de red, abra también el [puerto correcto](#bkmk_openports) para el depurador remoto (4024 o 4022). De este modo, no tendrá que abrirlo más adelante. Si utiliza Web Deploy, abra también el puerto 8172.

### <a name="update-browser-security-settings-on-windows-server"></a>Actualización de la configuración de seguridad del explorador en Windows Server

Si la opción Configuración de seguridad mejorada está habilitada en Internet Explorer (lo está de forma predeterminada), es posible que tenga que agregar algunos dominios como sitios de confianza para poder descargar algunos de los componentes del servidor web. Para agregar los sitios de confianza, vaya a **Opciones de Internet > Seguridad > Sitios de confianza > Sitios**. Agregue los dominios siguientes.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

Al descargar el software, es posible que reciba solicitudes para conceder permiso con el fin de cargar varios scripts y recursos de los sitios web. Algunos de estos recursos no son necesarios, pero para simplificar el proceso, haga clic en **Agregar** cuando se le solicite.

### <a name="install-aspnet-core-on-windows-server"></a>Instalación de ASP.NET Core en Windows Server

1. Instale el conjunto de hospedaje de .NET Core en el sistema de hospedaje. El lote instala .NET Core Runtime, .NET Core Library y el módulo ASP.NET Core. Para obtener más instrucciones detalladas, vea [Publicación en IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    En el caso de .NET Core 3, instale el [conjunto de hospedaje de .NET Core](https://dotnet.microsoft.com/permalink/dotnetcore-current-windows-runtime-bundle-installer).
    En el caso de .NET Core 2, instale el [hospedaje de .NET Core Windows Server](https://aka.ms/dotnetcore-2-windowshosting).

    > [!NOTE]
    > Si el sistema no tiene conexión a Internet, obtenga e instale *[Microsoft Visual C++ 2015 Redistributable](https://www.microsoft.com/download/details.aspx?id=53840)* antes de instalar el lote de hospedaje .NET Core Windows Server.

3. Reinicie el sistema (o ejecute **net stop was /y** seguido de **net start w3svc** desde un símbolo del sistema para obtener un cambio en la ruta de acceso del sistema).

## <a name="choose-a-deployment-option"></a>Elección de una opción de implementación

Si necesita ayuda para implementar la aplicación en IIS, tenga en cuenta estas opciones:

* Para la implementación, cree un archivo de configuración de publicación en IIS e importe la configuración en Visual Studio. En algunos escenarios, es una manera rápida de implementar la aplicación. Al crear el archivo de configuración de publicación, los permisos se configuran de forma automática en IIS.

* Para la implementación, efectúe la publicación en una carpeta local y copie la salida mediante un método preferido en una carpeta de aplicación preparada en IIS.

## <a name="optional-deploy-using-a-publish-settings-file"></a>(Opcional) Implementación mediante un archivo de configuración de publicación

Puede usar esta opción para crear un archivo de configuración de publicación e importarlo en Visual Studio.

> [!NOTE]
> Este método de implementación utiliza Web Deploy, que debe instalarse en el servidor. Si quiere configurar Web Deploy de forma manual en lugar de importar la configuración, puede instalar Web Deploy 3.6 en lugar de Web Deploy 3.6 para servidores de hospedaje. Pero si configura Web Deploy de forma manual, tendrá que asegurarse de que una carpeta de aplicación del servidor esté configurada con los valores y permisos correctos; vea [Instalación de ASP.NET 4.5 en Windows Server](#BKMK_deploy_asp_net).

### <a name="configure-the-aspnet-core-web-site"></a>Configuración del sitio web de ASP.NET Core

1. En el Administrador de IIS, en el panel izquierdo situado en **Conexiones**, seleccione **Grupos de aplicaciones**. Abra **DefaultAppPool** y establezca la **Versión de .NET CLR** en **Sin código administrado**. Es necesario para ASP.NET Core. El sitio web predeterminado utiliza DefaultAppPool.

2. Detenga y reinicie el grupo DefaultAppPool.

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Instalación y configuración de Web Deploy para servidores de hospedaje en Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Crear el archivo de configuración de publicación en IIS en Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importar la configuración de publicación a Visual Studio e implementar

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

> [!NOTE]
> Si reinicia una máquina virtual de Azure, la dirección IP puede cambiar.

Después de que se implemente la aplicación correctamente, debería iniciarse automáticamente. Si la aplicación no se inicia desde Visual Studio, iníciela en IIS para comprobar que se ejecuta correctamente. En ASP.NET Core, tiene que asegurarse también de que el campo Grupo de aplicaciones correspondiente a **DefaultAppPool** está establecido en **Sin código administrado**.

1. En el cuadro de diálogo **Configuración**, haga clic en **Siguiente** para habilitar la depuración, elija una configuración de **Depuración** y, después, en **Quitar archivos adicionales en destino** en las **Opciones de publicación de archivos**.

    > [!IMPORTANT]
    > Si elige una configuración de versión, deshabilite la depuración en el archivo *web.config* al realizar la publicación.

1. Haga clic en **Guardar** y, después, vuelva a publicar la aplicación.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(Opcional) Implementación mediante la publicación en una carpeta local

Puede usar esta opción para implementar la aplicación si desea copiarla en IIS con PowerShell, RoboCopy o si desea copiar manualmente los archivos.

### <a name="configure-the-aspnet-core-web-site-on-the-windows-server-computer"></a><a name="BKMK_deploy_asp_net"></a> Configuración del sitio web de ASP.NET Core en el equipo con Windows Server

Si va a importar la configuración de publicación, puede omitir esta sección.

1. Abra el **Administrador de Internet Information Services (IIS)** y vaya a **Sitios**.

2. Haga clic con el botón secundario en el nodo **Sitio web predeterminado** y seleccione **Agregar aplicación**.

3. Establezca el campo **Alias** en **MyASPApp** y el campo Grupo de aplicaciones, en **Sin código administrado**. Establezca la **ruta de acceso física** en **C:\Publish** (donde más adelante se implementará el proyecto de ASP.NET Core).

4. Con el sitio seleccionado en el Administrador IIS, elija **Editar permisos** y asegúrese de que IUSR, IIS_IUSRS o el usuario configurado para el acceso a la aplicación web sea un usuario autorizado con derechos Leer y ejecutar.

    Si no ve uno de estos usuarios con acceso, siga los pasos para agregar IUSR como usuario con derechos Leer y ejecutar.

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>(Opcional) Publicación e implementación de la aplicación mediante la publicación en una carpeta local desde Visual Studio

Si no está usando Web Deploy, debe publicar e implementar la aplicación con el sistema de archivos o con otras herramientas. Puede empezar creando un paquete con el sistema de archivos y, después, implementar el paquete manualmente o usar otras herramientas, como PowerShell, Robocopy o XCopy. En esta sección se da por hecho que copiará el paquete manualmente si no usa Web Deploy.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="download-and-install-the-remote-tools-on-windows-server"></a><a name="BKMK_msvsmon"></a> Descarga e instalación de las herramientas remotas en Windows Server

Descargue la versión de las herramientas remotas que corresponda a su versión de Visual Studio.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="set-up-the-remote-debugger-on-windows-server"></a><a name="BKMK_setup"></a> Establecimiento del depurador remoto en Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Si tiene que agregar permisos para usuarios adicionales, cambiar el modo de autenticación o el número de puerto para el depurador remoto, vea [Configuración del depurador remoto](../debugger/remote-debugging.md#configure_msvsmon).

### <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a><a name="BKMK_attach"></a> Adjuntar elementos a la aplicación ASP.NET desde el equipo de Visual Studio

1. En el equipo de Visual Studio, abra la solución que intenta depurar (**MyASPApp** si está siguiendo los pasos de este artículo).
2. En Visual Studio, haga clic en **Depurar > Asociar al proceso** (Ctrl + Alt + P).

    > [!TIP]
    > En Visual Studio 2017 y versiones posteriores, puede volver a asociar al mismo proceso al que ha asociado antes mediante **Depurar > Reasociar al proceso...** (Mayús+Alt+P).

3. Establezca el campo Calificador en **\<remote computer name>** y presione **Entrar**.

    Compruebe que Visual Studio agrega el puerto necesario al nombre del equipo, que aparece en el formato **\<remote computer name>:puerto**.

    ::: moniker range=">=vs-2019"
    En Visual Studio 2019, debería ver **\<remote computer name>:4024**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    En Visual Studio 2017, debería ver **\<remote computer name>:4022**.
    ::: moniker-end
    El puerto es obligatorio. Si no ve el número de puerto, agréguelo manualmente.

4. Haga clic en **Actualizar**.
    Debería ver que algunos procesos aparecen en la ventana **Procesos disponibles** .

    Si no ve ningún proceso, pruebe a usar la dirección IP en lugar del nombre del equipo remoto (el puerto es obligatorio). Puede usar `ipconfig` en una línea de comandos para obtener la dirección IPv4.

    Si desea usar el botón **Buscar**, es posible que deba [abrir el puerto UDP 3702](#bkmk_openports) en el servidor.

5. Active  **Mostrar los procesos de todos los usuarios**.

6. Escriba la primera letra del nombre del proceso para encontrar rápidamente la aplicación.

    * Si usa el [modelo de hospedaje en proceso](/aspnet/core/host-and-deploy/aspnet-core-module?view=aspnetcore-3.1&preserve-view=true#hosting-models) en IIS, seleccione el proceso **w3wp.exe** correcto. A partir de .NET Core 3, este es el valor predeterminado.

    * De lo contrario, seleccione el proceso **dotnet.exe**. (Este es el modelo de hospedaje fuera de proceso).

    Si tiene varios procesos que muestran *w3wp.exe* o *dotnet.exe*, compruebe la columna **Nombre de usuario**. En algunos escenarios, en la columna **Nombre de usuario** se muestra el nombre del grupo de aplicaciones, como **IIS APPPOOL\DefaultAppPool**. Si ve el grupo de aplicaciones, pero no es único, cree uno con nombre para la instancia de la aplicación que quiera depurar y, después, lo podrá encontrar fácilmente en la columna **Nombre de usuario**.

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. Haga clic en **Adjuntar**.

8. Abra el sitio web del equipo remoto. En un explorador, vaya a **http://\<remote computer name>** .

    Debería ver la página web de ASP.NET.
9. En la aplicación de ASP.NET en ejecución, haga clic en el vínculo a la página **Acerca de**.

    Se alcanzará el punto de interrupción en Visual Studio.

### <a name="troubleshooting-open-required-ports-on-windows-server"></a><a name="bkmk_openports"></a> Solución de problemas: apertura de los puertos obligatorios en Windows Server

En la mayoría de las instalaciones, los puertos obligatorios se abren mediante la instalación de ASP.NET y el depurador remoto. Pero si está solucionando problemas de implementación y la aplicación se hospeda detrás de un firewall, puede que tenga que comprobar que están abiertos los puertos correctos.

En una máquina virtual de Azure, debe abrir los puertos a través del [grupo de seguridad de red](/azure/virtual-machines/windows/nsg-quickstart-portal).

Puertos necesarios:

* 80: obligatorio para IIS
::: moniker range=">=vs-2019"
* 4024: obligatorio para la depuración remota desde Visual Studio 2019 (vea [Asignaciones de puertos del depurador remoto](../debugger/remote-debugger-port-assignments.md) para obtener más información).
::: moniker-end
::: moniker range="vs-2017"
* 4022: obligatorio para la depuración remota desde Visual Studio 2017 (vea [Asignaciones de puertos del depurador remoto](../debugger/remote-debugger-port-assignments.md) para obtener más información).
::: moniker-end
* UDP 3702: (opcional) El puerto de detección habilita el botón **Buscar** al asociarse al depurador remoto en Visual Studio.

Además, estos puertos ya deberían estar abiertos por la instalación de ASP.NET:
- 8172: (opcional) Necesario para que Web Deploy implemente la aplicación desde Visual Studio
