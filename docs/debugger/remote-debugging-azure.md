---
title: ASP.NET Core de depuración remota en IIS y Azure | Microsoft Docs
ms.custom: remotedebugging
ms.date: 05/21/2018
ms.topic: conceptual
ms.assetid: a6c04b53-d1b9-4552-a8fd-3ed6f4902ce6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
- dotnetcore
- azure
ms.openlocfilehash: c6a41a332e16f79673b475404af27e540689938d
ms.sourcegitcommit: 3d64bfb9bf85395357effe054db9a9afaa0be5ea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/29/2020
ms.locfileid: "78181134"
---
# <a name="remote-debug-aspnet-core-on-iis-in-azure-in-visual-studio"></a>Depuración remota ASP.NET Core en IIS en Azure en Visual Studio

En esta guía se explica cómo configurar y configurar una aplicación de ASP.NET Core de Visual Studio, implementarla en IIS con Azure y asociar el depurador remoto desde Visual Studio.

El método recomendado para la depuración remota en Azure depende del escenario:

* Para depurar ASP.NET Core en Azure App Service, vea [depurar aplicaciones de Azure con el Snapshot Debugger](../debugger/debug-live-azure-applications.md). Éste es el método recomendado.
* Para depurar ASP.NET Core en Azure App Service mediante las características de depuración más tradicionales, siga los pasos de este tema (vea la sección [depuración remota en Azure App Service](#remote_debug_azure_app_service)).

    En este escenario, debe implementar la aplicación desde Visual Studio en Azure, pero no es necesario instalar o configurar manualmente IIS o el depurador remoto (estos componentes se representan con líneas de puntos), tal como se muestra en la siguiente ilustración.

    ![Componentes del Depurador remoto](../debugger/media/remote-debugger-azure-app-service.png "Remote_debugger_components")

* Para depurar IIS en una máquina virtual de Azure, siga los pasos de este tema (consulte la sección [depuración remota en una máquina virtual de Azure](#remote_debug_azure_vm)). Esto le permite usar una configuración personalizada de IIS, pero los pasos de instalación e implementación son más complicados.

    En el caso de una máquina virtual de Azure, debe implementar la aplicación desde Visual Studio en Azure y también debe instalar manualmente el rol de IIS y el depurador remoto, tal como se muestra en la siguiente ilustración.

    ![Componentes del Depurador remoto](../debugger/media/remote-debugger-azure-vm.png "Remote_debugger_components")

* Para depurar ASP.NET Core en Azure Service Fabric, consulte [depurar una aplicación de Service fabric remota](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application).

> [!WARNING]
> Asegúrese de eliminar los recursos de Azure que cree cuando haya completado los pasos de este tutorial. De este modo, puede evitar incurrir en cargos innecesarios.

## <a name="prerequisites"></a>Prerequisites

::: moniker range=">=vs-2019"
Visual Studio 2019 es necesario para seguir los pasos que se muestran en este artículo.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017 es necesario para seguir los pasos que se muestran en este artículo.
::: moniker-end

### <a name="network-requirements"></a>Requisitos de red

No se admite la depuración entre dos equipos conectados a través de un proxy. No se recomienda la depuración a través de una conexión de alta latencia o de ancho de banda bajo, como acceso telefónico a Internet o a través de Internet a través de países, y puede producir un error o ser inaceptablemente lento. Para obtener una lista completa de los requisitos, consulte [requisitos](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Crear la aplicación ASP.NET Core en el equipo de Visual Studio

1. Cree una nueva aplicación ASP.NET Core.

    ::: moniker range=">=vs-2019"
    En Visual Studio 2019, escriba **Ctrl + Q** para abrir el cuadro de búsqueda, escriba **ASP.net**, elija **plantillas**y, a continuación, elija **crear nuevo ASP.net Core aplicación web**. En el cuadro de diálogo que aparece, asigne al proyecto el nombre **MyASPApp**y, a continuación, elija **crear**. A continuación, elija **aplicación web (controlador de vista de modelo)** y, a continuación, elija **crear**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    En Visual Studio 2017, elija **archivo > nuevo > proyecto**y, a continuación, seleccione **Visual C# > Web > ASP.net Core aplicación web**. En la sección plantillas de ASP.NET Core, seleccione **aplicación web (Model-View-Controller)** . Asegúrese de que se ha seleccionado ASP.NET Core 2,1, que no está seleccionada la opción **Habilitar compatibilidad con Docker** y que la **autenticación** está establecida en **sin autenticación**. Asigne al proyecto el nombre **MyASPApp**.
    ::: moniker-end

1. Abra el archivo About.cshtml.cs y establezca un punto de interrupción en el método `OnGet` (en las plantillas anteriores, abra HomeController.cs en su lugar y establezca el punto de interrupción en el método `About()`).

## <a name="remote_debug_azure_app_service"></a>ASP.NET Core de depuración remota en un Azure App Service

Desde Visual Studio, puede publicar y depurar rápidamente la aplicación en una instancia totalmente aprovisionada de IIS. Sin embargo, la configuración de IIS está preestablecida y no se puede personalizar. Para obtener instrucciones más detalladas, consulte [implementación de una aplicación Web de ASP.net Core en Azure con Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). (Si necesita la capacidad de personalizar IIS, pruebe a depurar en una [máquina virtual de Azure](#remote_debug_azure_vm)).

#### <a name="to-deploy-the-app-and-remote-debug-using-server-explorer"></a>Para implementar la aplicación y la depuración remota con Explorador de servidores

1. En Visual Studio, haga clic con el botón derecho en el nodo del proyecto y elija **publicar**.

    Si previamente ha configurado algún perfil de publicación, aparece el panel **Publicar**. Haga clic en **nuevo perfil**.

1. Elija **Azure App Service** en el cuadro de diálogo **publicar** , seleccione **crear nuevo**y siga las indicaciones para publicar.

    Para obtener instrucciones detalladas, vea [Publicar una aplicación de ASP.NET Core en Azure con Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

    ![Publicar en Azure App Service](../debugger/media/remotedbg_azure_app_service_profile.png)

1. Abra **Explorador de servidores** (**Ver** > **Explorador de servidores**), haga clic con el botón derecho en la instancia de App Service y elija **asociar depurador**.

1. En la aplicación ASP.NET en ejecución, haga clic en el vínculo a la página **About** .

    Se alcanzará el punto de interrupción en Visual Studio.

    Eso es todo. El resto de los pasos de este tema se aplican a la depuración remota en una máquina virtual de Azure.

## <a name="remote_debug_azure_vm"></a>ASP.NET Core de depuración remota en una máquina virtual de Azure

Puede crear una máquina virtual de Azure para Windows Server y, a continuación, instalar y configurar IIS y los demás componentes de software necesarios. Esto supone más tiempo que la implementación en un Azure App Service y requiere que siga los pasos restantes de este tutorial.

Estos procedimientos se han probado en estas configuraciones de servidor:
* Windows Server 2012 R2 e IIS 8
* Windows Server 2016 e IIS 10

### <a name="app-already-running-in-iis-on-the-azure-vm"></a>¿La aplicación ya se está ejecutando en IIS en la máquina virtual de Azure?

En este artículo se incluyen los pasos para configurar una configuración básica de IIS en Windows Server e implementar la aplicación desde Visual Studio. Estos pasos se incluyen para asegurarse de que el servidor tiene instalados los componentes necesarios, que la aplicación se puede ejecutar correctamente y que está listo para la depuración remota.

* Si la aplicación se ejecuta en IIS y solo desea descargar el depurador remoto e iniciar la depuración, vaya a [Descargar e instalar las herramientas remotas en Windows Server](#BKMK_msvsmon).

* Si desea obtener ayuda para asegurarse de que la aplicación está configurada, implementada y ejecutándose correctamente en IIS para que pueda depurar, siga todos los pasos de este tema.

  * Antes de comenzar, siga todos los pasos descritos en [instalar y ejecutar IIS](/azure/virtual-machines/windows/quick-create-portal).

  * Al abrir el puerto 80 en el grupo de seguridad de red, abra también el [puerto correcto](#bkmk_openports) para el depurador remoto (4024 o 4022). De este modo, no tendrá que abrirlo más adelante.

### <a name="update-browser-security-settings-on-windows-server"></a>Actualizar la configuración de seguridad del explorador en Windows Server

Si la opción Configuración de seguridad mejorada está habilitada en Internet Explorer (está habilitada de forma predeterminada), es posible que deba agregar algunos dominios como sitios de confianza para poder descargar algunos de los componentes de servidor Web. Para agregar sitios de confianza, vaya a **Opciones de Internet > seguridad > sitios de confianza > sitios**. Agregue los siguientes dominios.

- microsoft.com
- go.microsoft.com
- download.Microsoft.com
- iis.net

Al descargar el software, puede recibir solicitudes para conceder permiso para cargar varios scripts y recursos de sitios Web. Algunos de estos recursos no son necesarios, pero para simplificar el proceso, haga clic en **Agregar** cuando se le solicite.

### <a name="install-aspnet-core-on-windows-server"></a>Instalación de ASP.NET Core en Windows Server

1. Instale el lote de [hospedaje .NET Core Windows Server](https://aka.ms/dotnetcore-2-windowshosting) en el sistema host. El lote instala .NET Core Runtime, .NET Core Library y el módulo ASP.NET Core. Para obtener instrucciones más detalladas, vea [publicar en IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    > [!NOTE]
    > Si el sistema no tiene conexión a Internet, obtenga e instale *[Microsoft Visual C++ 2015 Redistributable](https://www.microsoft.com/download/details.aspx?id=53840)* antes de instalar el lote de hospedaje .NET Core Windows Server.

3. Reinicie el sistema (o ejecute **net stop was /y** seguido de **net start w3svc** desde un símbolo del sistema para obtener un cambio en la ruta de acceso del sistema).

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

Después de que se implemente la aplicación correctamente, debería iniciarse automáticamente. Si la aplicación no se inicia desde Visual Studio, inicie la aplicación en IIS. Para ASP.NET Core, deberá asegurarse de que el campo Grupo de aplicaciones para el **DefaultAppPool** está establecido en **Sin código administrado**.

1. En el cuadro de diálogo **configuración** , habilite la depuración; para ello, haga clic en **siguiente**, elija una configuración de **depuración** y, a continuación, elija **quitar archivos adicionales en destino** en opciones de **publicación de archivos** .

    > [!NOTE]
    > Si elige una configuración de versión, deshabilite la depuración en el archivo *Web. config* al publicar.

1. Haga clic en **Guardar** y, a continuación, vuelva a publicar la aplicación.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>Opta Implementación mediante la publicación en una carpeta local

Puede usar esta opción para implementar la aplicación si quiere copiar la aplicación en IIS con PowerShell, RoboCopy o desea copiar manualmente los archivos.

### <a name="BKMK_deploy_asp_net"></a>Configurar el sitio web de ASP.NET Core en el equipo con Windows Server

Si va a importar la configuración de publicación, puede omitir esta sección.

1. Abra el **Administrador de Internet Information Services (IIS)** y vaya a **Sitios**.

2. Haga clic con el botón secundario en el nodo **Sitio web predeterminado** y seleccione **Agregar aplicación**.

3. Establezca el campo **alias** en **MyASPApp** y el campo Grupo de aplicaciones en **sin código administrado**. Establezca la **ruta de acceso física** en **C:\Publish** (donde se implementará más adelante el proyecto ASP.net Core).

4. Con el sitio seleccionado en el administrador de IIS, elija **Editar permisos**y asegúrese de que IUSR, IIS_IUSRS o el usuario configurado para el grupo de aplicaciones sea un usuario autorizado con derechos de lectura & ejecución.

    Si no ve uno de estos usuarios con acceso, siga los pasos para agregar IUSR como usuario con derechos de lectura & ejecución.

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Opta Publicar e implementar la aplicación mediante la publicación en una carpeta local desde Visual Studio

Si no está usando Web Deploy, debe publicar e implementar la aplicación con el sistema de archivos u otras herramientas. Puede empezar por crear un paquete con el sistema de archivos y, a continuación, implementar el paquete manualmente o usar otras herramientas como PowerShell, RoboCopy o XCopy. En esta sección, se supone que está copiando manualmente el paquete si no está usando Web Deploy.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="BKMK_msvsmon"></a>Descargar e instalar las herramientas remotas en Windows Server

Descargue la versión de las herramientas remotas que coincida con su versión de Visual Studio.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="BKMK_setup"></a> Establecimiento del depurador remoto en Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Si necesita agregar permisos para usuarios adicionales, cambie el modo de autenticación o el número de puerto para el depurador remoto, vea [configurar el depurador remoto](../debugger/remote-debugging.md#configure_msvsmon).

### <a name="BKMK_attach"></a> Adjuntar elementos a la aplicación ASP.NET desde el equipo de Visual Studio

1. En el equipo de Visual Studio, abra la solución que está intentando depurar (**MyASPApp** si está siguiendo los pasos descritos en este artículo).
2. En Visual Studio, haga clic en **Depurar > asociar al proceso** (Ctrl + Alt + P).

    > [!TIP]
    > En Visual Studio 2017 y versiones posteriores, puede volver a adjuntar al mismo proceso al que adjuntó anteriormente mediante **Depurar > reasociar al proceso...** (Mayús + Alt + P).

3. Establezca el campo calificador en **\<nombre de equipo remoto >** y presione **entrar**.

    Compruebe que Visual Studio agrega el puerto necesario al nombre del equipo, que aparece en el formato: **\<nombre de equipo remoto >:p ordenar**

    ::: moniker range=">=vs-2019"
    En Visual Studio 2019, debería ver **\<nombre de equipo remoto >: 4024**
    ::: moniker-end
    ::: moniker range="vs-2017"
    En Visual Studio 2017, debería ver **\<nombre de equipo remoto >: 4022**
    ::: moniker-end
    El puerto es obligatorio. Si no ve el número de puerto, agréguelo manualmente.

4. Haga clic en **Actualizar**.
    Debería ver que algunos procesos aparecen en la ventana **Procesos disponibles** .

    Si no ve ningún proceso, pruebe a usar la dirección IP en lugar del nombre del equipo remoto (el puerto es obligatorio). Puede usar `ipconfig` en una línea de comandos para obtener la dirección IPv4.

    Si desea usar el botón **Buscar** , puede que necesite [abrir el puerto UDP 3702](#bkmk_openports) en el servidor.

5. Active  **Mostrar los procesos de todos los usuarios**.

6. Escriba la primera letra del nombre del proceso para encontrar rápidamente la aplicación.

    * Seleccione **dotnet. exe** (para .net Core)

      Si tiene varios procesos que muestran **dotnet. exe**, Compruebe la columna **nombre de usuario** . En algunos escenarios, la columna **nombre de usuario** muestra el nombre del grupo de aplicaciones, como **IIS APPPOOL\DefaultAppPool**. Si ve el grupo de aplicaciones, una manera fácil de identificar el proceso correcto es crear un nuevo grupo de aplicaciones con nombre para la instancia de la aplicación que desea depurar y, a continuación, puede encontrarlo fácilmente en la columna **nombre de usuario** .

    * En algunos escenarios de IIS, puede encontrar el nombre de la aplicación en la lista de procesos, como **MyASPApp. exe**. En su lugar, puede adjuntar a este proceso.

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. Haga clic en **Adjuntar**.

8. Abra el sitio web del equipo remoto. En un explorador, vaya a **http://\<nombre del equipo remoto>** .

    Debería ver la página web de ASP.NET.
9. En la aplicación ASP.NET en ejecución, haga clic en el vínculo a la página **About** .

    Se alcanzará el punto de interrupción en Visual Studio.

### <a name="bkmk_openports"></a> Solución de problemas Abra los puertos necesarios en Windows Server

En la mayoría de las instalaciones, los puertos necesarios se abren mediante la instalación de ASP.NET y el depurador remoto. Sin embargo, si está solucionando problemas de implementación y la aplicación se hospeda detrás de un firewall, puede que tenga que comprobar que están abiertos los puertos correctos.

En una máquina virtual de Azure, debe abrir los puertos a través del [grupo de seguridad de red](/azure/virtual-machines/windows/nsg-quickstart-portal).

Puertos necesarios:

* 80: necesario para IIS
::: moniker range=">=vs-2019"
* 4024: necesario para la depuración remota desde Visual Studio 2019 (vea [asignaciones de puerto del Depurador remoto](../debugger/remote-debugger-port-assignments.md) para obtener más información).
::: moniker-end
::: moniker range="vs-2017"
* 4022: necesario para la depuración remota desde Visual Studio 2017 (vea [asignaciones de puerto del Depurador remoto](../debugger/remote-debugger-port-assignments.md) para obtener más información).
::: moniker-end
* UDP 3702: (opcional) el puerto de detección permite el botón **Buscar** al asociarse al depurador remoto en Visual Studio.

Además, estos puertos ya deben estar abiertos por la instalación de ASP.NET:
- 8172: (opcional) necesario para que Web Deploy implementar la aplicación desde Visual Studio
