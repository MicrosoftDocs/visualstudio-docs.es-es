---
title: Remoto depurar Core de ASP.NET en IIS y Azure | Documentos de Microsoft
ms.custom: remotedebugging
ms.date: 08/14/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a6c04b53-d1b9-4552-a8fd-3ed6f4902ce6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
- dotnetcore
- azure
ms.openlocfilehash: c95a91ecd057bfec7af5e9b932d4326cdcab9270
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/11/2018
---
# <a name="remote-debug-aspnet-core-on-iis-in-azure-in-visual-studio-2017"></a>Depuración remota de núcleo de ASP.NET en IIS en Azure en Visual Studio de 2017

Esta guía explica cómo instalar y configurar una aplicación de Visual Studio de 2017 ASP.NET Core, implementarla en IIS con Azure y asociar al depurador remoto de Visual Studio.

El método recomendado para realizar la depuración remota en Azure depende de su escenario:

* Para depurar ASP.NET Core en servicio de aplicaciones de Azure, consulte [aplicaciones de Azure depurar con el depurador de instantánea](../debugger/debug-live-azure-applications.md). Este es el método recomendado.
* Para depurar ASP.NET Core en usar las características de depuración más tradicionales de servicio de aplicaciones de Azure, siga los pasos de este tema (vea la sección [de depuración remota en el servicio de aplicaciones de Azure](#remote_debug_azure_app_service)).

    En este escenario, debe implementar la aplicación desde Visual Studio en Azure pero no es necesario instalar manualmente o configurar IIS o el depurador remoto (estos componentes se representan con líneas de puntos), como se muestra en la siguiente ilustración.

    ![Los componentes del depurador remoto](../debugger/media/remote-debugger-azure-app-service.png "Remote_debugger_components")

* Para depurar IIS en una VM de Azure, siga los pasos descritos en este tema (vea la sección [la depuración remota en una máquina virtual de Azure](#remote_debug_azure_vm)). Esto le permite usar una configuración personalizada de IIS, pero los pasos de instalación e implementación son más complicados.

    Para una máquina virtual de Azure, debe implementar la aplicación desde Visual Studio en Azure y también debe instalar manualmente el rol IIS y el depurador remoto, tal como se muestra en la siguiente ilustración.

    ![Los componentes del depurador remoto](../debugger/media/remote-debugger-azure-vm.png "Remote_debugger_components")

* Para depurar ASP.NET Core en Azure Service Fabric, vea [depurar una aplicación de Service Fabric remota](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application).

> [!WARNING]
> Asegúrese de eliminar los recursos de Azure que se crea cuando se hayan completado los pasos de este tutorial. De este modo que puede evitar incurrir en cargos innecesarios.


### <a name="requirements"></a>Requisitos

No se admite la depuración entre dos equipos conectados a través de un servidor proxy. Depuración mediante una conexión de poco ancho de banda, como acceso telefónico a Internet, o una latencia alta o a través de Internet a través de países no se recomienda y puede ser un error o inaceptablemente bajo. Para obtener una lista completa de requisitos, consulte [requisitos](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="create-the-aspnet-core-application-on-the-visual-studio-2017-computer"></a>Crear la aplicación de ASP.NET Core en el equipo de Visual Studio de 2017 

1. Cree una nueva aplicación de ASP.NET Core. (Elija **archivo > Nuevo > proyecto**, a continuación, seleccione **Visual C# > Web > aplicación Web de ASP.NET Core**).

    En el **ASP.NET Core** sección plantillas, seleccione **aplicación Web**.

2. Asegúrese de que **ASP.NET Core 2.0** está seleccionada, que **habilitar la compatibilidad con Docker** es **no** seleccionada y que **autenticación** está establecido en **Sin autenticación**.

3. Denomine el proyecto **MyASPApp** y haga clic en **Aceptar** para crear la nueva solución.

4. Abra el archivo About.cshtml.cs y establecer un punto de interrupción en la `OnGet` (método) (en las plantillas anteriores, abra HomeController.cs en su lugar y establecer el punto de interrupción en el `About()` método).

## <a name="remote_debug_azure_app_service"></a> Núcleo de ASP.NET de depuración remota en un servicio de aplicaciones de Azure

Desde Visual Studio, puede publicar rápidamente y depurar la aplicación a una instancia de aprovisionamiento completo de IIS. Sin embargo, la configuración de IIS está predefinida y no es posible personalizar. Para obtener instrucciones detalladas, consulte [implementar una aplicación web de ASP.NET Core en Azure con Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). (Si necesita la capacidad de personalizar IIS, intentar depurar un [Azure VM](#BKMK_azure_vm).) 

#### <a name="to-deploy-the-app-and-remote-debug-using-server-explorer"></a>Para implementar la aplicación y la depuración remota mediante el Explorador de servidores

1. En Visual Studio, haga clic en el nodo del proyecto y elija **publicar**.

2. Elija **servicio de aplicaciones de Microsoft Azure** desde el **publicar** cuadro de diálogo, seleccione **crear nuevo**y siga las indicaciones para publicar.

    Para obtener instrucciones detalladas, consulte [implementar una aplicación web de ASP.NET Core en Azure con Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

3. Abra **Explorador de servidores** (**vista** > **Explorador de servidores**), haga doble clic en la instancia de servicio de aplicaciones y elija **adjuntar depurador**.

4. En la aplicación ASP.NET en ejecución, haga clic en el vínculo a la **sobre** página.

    Se alcanzará el punto de interrupción en Visual Studio.

    Ya está. El resto de los pasos descritos en este tema se aplican a la depuración remota en una máquina virtual de Azure.

## <a name="remote_debug_azure_vm"></a> Núcleo de ASP.NET de depuración remota en una máquina virtual de Azure

Puede crear una máquina virtual de Azure para Windows Server y, a continuación, instalar y configurar IIS y los demás componentes de software necesarias. Esto es más lento que la implementación en un servicio de aplicaciones de Azure y requiere que siga los pasos restantes de este tutorial.

En primer lugar, siga los pasos descritos en [instale y ejecute IIS](/azure/virtual-machines/windows/quick-create-portal).

Al abrir el puerto 80 en el grupo de seguridad de red, abrir el puerto 4022 para que el depurador remoto. De este modo, no tendrá que abrirla más tarde.

### <a name="update-browser-security-settings-on-windows-server"></a>Actualizar la configuración de seguridad del explorador en Windows Server

Según la configuración de seguridad del explorador, puede ahorrar tiempo para agregar los siguientes sitios de confianza en el explorador, por lo que puede descargar más rápidamente el software descrito en este tutorial. Puede ser necesario tener acceso a estos sitios:

- Microsoft.com
- go.microsoft.com
- download.microsoft.com
- visualstudio.com
- IIS.NET

Si está usando Internet Explorer, puede agregar los sitios de confianza, vaya a **opciones de Internet > seguridad > sitios de confianza > sitios**. Estos pasos son diferentes para otros exploradores. (Si tiene que descargar una versión anterior del depurador remoto de my.visualstudio.com, algunos sitios de confianza adicionales son necesarios para iniciar sesión).

Al descargar el software, puede obtener las solicitudes para conceder permiso para cargar varias secuencias de comandos del sitio web y recursos. En la mayoría de los casos, estos recursos adicionales no son necesarios para instalar el software.

### <a name="install-aspnet-core-on-windows-server"></a>Instalar ASP.NET Core en Windows Server

1. Instalar el [hospedaje de .NET Core Windows Server](https://aka.ms/dotnetcore-2-windowshosting) agrupación en el sistema host. La agrupación instalará el tiempo de ejecución de .NET Core, biblioteca principal de .NET y el módulo de núcleo de ASP.NET. Para obtener instrucciones más detalladas, consulte [publicar en IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    > [!NOTE]
    > Si el sistema no tiene una conexión a Internet, obtenga e instale el *[Microsoft Visual C++ 2015 Redistributable](https://www.microsoft.com/download/details.aspx?id=53840)* antes de instalar el paquete de hospedaje de .NET Core Windows Server.

3. Reiniciar el sistema (o ejecutar **net stop era /y** seguido **del comando net start w3svc** desde un símbolo del sistema para recoger un cambio en la ruta de acceso del sistema).

## <a name="optional-install-web-deploy-36-for-hosting-servers-on-windows-server"></a>(Opcional) Instale WebDeploy 3.6 para hospedar servidores en Windows Server

En algunos casos, puede ser más rápido para importar configuración de publicación en Visual Studio en lugar de configurar manualmente opciones de implementación. Si prefiere importar configuración en lugar de configurar el perfil de publicación en Visual Studio de publicación, vea [importar configuración de publicación e implementar a IIS](../deployment/tutorial-import-publish-settings-iis.md). En caso contrario, permanezca en este tema y siga leyendo. Si completó el artículo sobre la importación de configuración de publicación e implementar correctamente, la aplicación, a continuación, vuelva a este tema e iniciar en la sección en [descargar las herramientas remotas](#BKMK_msvsmon).

### <a name="BKMK_install_webdeploy"></a> (Opcional) Instale WebDeploy 3.6 en Windows Server

[!INCLUDE [remote-debugger-install-web-deploy](../debugger/includes/remote-debugger-install-web-deploy.md)]

### <a name="BKMK_deploy_asp_net"></a> Configurar el sitio Web de ASP.NET en el equipo de Windows Server

Si va a importar la configuración de publicación, puede omitir esta sección.

1. Abra el **Administrador de Internet Information Services (IIS)** y vaya a **Sitios**.

2. Haga clic con el botón secundario en el nodo **Sitio web predeterminado** y seleccione **Agregar aplicación**.

3. Establecer el **Alias** campo **MyASPApp** y el campo de grupo de aplicaciones a **sin código administrado**. Establecer el **ruta de acceso física** a **C:\Publish** (donde posteriormente implementará el proyecto ASP.NET).

4. Con el sitio seleccionado en el Administrador de IIS, elija **Editar permisos**y asegúrese de que ese IUSR, IIS_IUSRS o el usuario configurado para el grupo de aplicaciones es un usuario autorizado con permisos de lectura y ejecución.

    Si no ve uno de estos usuarios con acceso, vaya a través de los pasos necesarios para agregar IUSR como un usuario con derechos de lectura y ejecución.

### <a name="bkmk_webdeploy"></a> (Opcional) Publique e implemente la aplicación mediante Web Deploy desde Visual Studio

Si ha instalado Web Deploy mediante el instalador de plataforma Web, puede implementar la aplicación directamente desde Visual Studio.

1. Inicie Visual Studio con privilegios elevados y vuelva a abrir el proyecto.

    Esto puede ser necesario para implementar la aplicación mediante Web Deploy.

2. En el **Explorador de soluciones**, haga clic con el botón secundario en el nodo del proyecto y seleccione **Publicar**.

3. Para **seleccionar un destino de publicación**, seleccione **Máquina Virtual de Microsoft Azure** y haga clic en **publicar**.

    ![RemoteDBG_Publish_IISl](../debugger/media/remotedbg_azure_vm_profile.png "RemoteDBG_Publish_IIS")

4. En el cuadro de diálogo, seleccione la máquina virtual de Azure que creó anteriormente.

4. Especifique los parámetros de configuración de corrección para el programa de instalación de la máquina virtual de Azure e IIS.

    ![RemoteDBG_Publish_WebDeployl](../debugger/media/remotedbg_iis_webdeploy_config.png "RemoteDBG_Publish_WebDeploy")

    Si no resuelve un nombre de host al intentar validar en los siguientes pasos el **Server** texto cuadro, pruebe la dirección IP. Asegúrese de que utiliza el puerto 80 en el **Server** texto cuadro y asegúrese de que el puerto 80 está abierto en el firewall.

6. Haga clic en **siguiente**, elija un **depurar** configuración y elija **quitar archivos adicionales en destino** en el **publicar archivos** Opciones.

5. Haga clic en **Prev**y, a continuación, elija **validar**. Si se valida la configuración de la conexión, puede intentar publicar.

6. Haga clic en **publicar** para publicar la aplicación.

    La ficha salida le mostrará si la publicación sea correcta y que el explorador abrirá la aplicación.

    Si se produce un error que haga mención Web Deploy, vuelva a comprobar los pasos de instalación de Web Deploy y asegúrese de que el [correcta puertos están abiertos](#bkmk_openports) están en el servidor.

    Si la aplicación se implementa correctamente, pero no se ejecuta correctamente, vuelva a comprobar que IIS y el proyecto de Visual Studio usa la misma versión de ASP.NET. Si es no el problema, puede haber un problema con la configuración de IIS o la configuración del sitio Web. En el servidor de Windows, abra el sitio Web de IIS para los mensajes de error más específicos y, a continuación, volver a comprobar los pasos anteriores.

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>(Opcional) Publique e implemente la aplicación al realizar la publicación en una carpeta local de Visual Studio

Si no usa Web Deploy, debe publicar e implementar la aplicación mediante el sistema de archivos u otras herramientas. Puede iniciar mediante la creación de un paquete mediante el sistema de archivos y, a continuación, implementar manualmente el paquete o usar otras herramientas, como XCopy, RoboCopy o PowerShell. En esta sección, se supone que va a copiar manualmente el paquete si no se utiliza Web Deploy.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="BKMK_msvsmon"></a> Descargue e instale las herramientas remotas en Windows Server

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
### <a name="BKMK_setup"></a> Configurar el depurador remoto en Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Si necesita agregar permisos para los usuarios adicionales, cambiar el modo de autenticación o número de puerto para el depurador remoto, consulte [configurar el depurador remoto](../debugger/remote-debugging.md#configure_msvsmon).

### <a name="BKMK_attach"></a> Adjuntar elementos a la aplicación ASP.NET desde el equipo de Visual Studio

1. En el equipo de Visual Studio, abra el **MyASPApp** solución.
2. En Visual Studio, haga clic en **Depurar > asociar al proceso** (Ctrl + Alt + P).

    > [!TIP]
    > En Visual Studio de 2017, puede volver a adjuntar al mismo proceso que ha asociado previamente a mediante el uso de **Depurar > volver a adjuntar al proceso...** (Mayús + Alt + P). 

3. Establezca el campo calificador en  **\<nombre del equipo remoto >: 4022**.
4. Haga clic en **Actualizar**.
    Debería ver que algunos procesos aparecen en la ventana **Procesos disponibles** .

    Si no ve todos los procesos, pruebe a usar la dirección IP en lugar del nombre del equipo remoto (el puerto es necesario). Puede usar `ipconfig` en una línea de comandos para obtener la dirección IPv4.

    Si desea utilizar el **buscar** botón, puede que necesite [abrir el puerto UDP 3702](#bkmk_openports) en el servidor.

5. Active  **Mostrar los procesos de todos los usuarios**.
6. Escriba la primera letra de un nombre de proceso para encontrar rápidamente **dotnet.exe** (para ASP.NET Core).
    >Nota: Para una aplicación ASP.NET Core, el nombre del proceso anterior era dnx.exe.

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg_attachtoprocess_aspnetcore.png "RemoteDBG_AttachToProcess")

7. Haga clic en **Adjuntar**.

8. Abra el sitio web del equipo remoto. En un explorador, vaya a **http://\<nombre del equipo remoto >**.
    
    Debería ver la página web de ASP.NET.
9. En la aplicación ASP.NET en ejecución, haga clic en el vínculo a la **sobre** página.

    Se alcanzará el punto de interrupción en Visual Studio.

### <a name="bkmk_openports"></a> Solución de problemas: Abra los puertos necesarios en Windows Server

En la mayoría de las instalaciones, se abren los puertos necesarios por la instalación de ASP.NET y el depurador remoto. Sin embargo, si está solucionando problemas de implementación y la aplicación se hospeda detrás de un firewall, debe comprobar que estén abiertos los puertos correctos.

En una máquina virtual de Azure, debe abrir puertos a través de la [grupo de seguridad de red](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80). 

Puertos necesarios:

- 80 - necesarias para IIS
- 4022 - necesarios para la depuración remota de Visual Studio de 2017 (vea [asignaciones de puerto de depurador remoto](../debugger/remote-debugger-port-assignments.md) para obtener más información).
- UDP 3702 - puerto de detección (opcional) permite la **buscar** botón al adjuntar el depurador remoto en Visual Studio.

Además, estos puertos deben abrirse ya mediante la instalación de ASP.NET:
- 8172 - (opcional) necesarios para que Web Deploy implementar la aplicación desde Visual Studio

