---
title: Remoto depurar Core de ASP.NET en IIS y Azure | Documentos de Microsoft
ms.custom: remotedebugging
ms.date: 05/21/2018
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
ms.openlocfilehash: a4e03f9a369959a5736d7030a1dac885771d7984
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34746772"
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

    Si previamente ha configurado ningún perfil de publicación, la **publicar** aparece el panel. Haga clic en **nuevo perfil**.

1. Elija **servicio de aplicaciones de Azure** desde el **publicar** cuadro de diálogo, seleccione **crear nuevo**y siga las indicaciones para publicar.

    Para obtener instrucciones detalladas, consulte [implementar una aplicación web de ASP.NET Core en Azure con Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

    ![Publicación en Azure App Service](../debugger/media/remotedbg_azure_app_service_profile.png)

1. Abra **Explorador de servidores** (**vista** > **Explorador de servidores**), haga doble clic en la instancia de servicio de aplicaciones y elija **adjuntar depurador**.

1. En la aplicación ASP.NET en ejecución, haga clic en el vínculo a la **sobre** página.

    Se alcanzará el punto de interrupción en Visual Studio.

    Ya está. El resto de los pasos descritos en este tema se aplican a la depuración remota en una máquina virtual de Azure.

## <a name="remote_debug_azure_vm"></a> Núcleo de ASP.NET de depuración remota en una máquina virtual de Azure

Puede crear una máquina virtual de Azure para Windows Server y, a continuación, instalar y configurar IIS y los demás componentes de software necesarias. Esto es más lento que la implementación en un servicio de aplicaciones de Azure y requiere que siga los pasos restantes de este tutorial.

En primer lugar, siga los pasos descritos en [instale y ejecute IIS](/azure/virtual-machines/windows/quick-create-portal).

Al abrir el puerto 80 en el grupo de seguridad de red, abrir el puerto 4022 para que el depurador remoto. De este modo, no tendrá que abrirla más tarde.

### <a name="app-already-running-in-iis-on-the-azure-vm"></a>¿Aplicación que se están ejecutando en IIS en la máquina virtual de Azure?

Este artículo incluye pasos sobre cómo configurar una configuración básica de IIS en Windows server y la implementación de la aplicación desde Visual Studio. Estos pasos se incluyen para asegurarse de que el servidor tiene los componentes necesarios de instalación, que la aplicación puede ejecutar correctamente y que está listo para realizar la depuración remota.

* Si la aplicación se ejecuta en IIS y desea descargar el depurador remoto y para iniciar la depuración, vaya a [descargar e instalar las herramientas remotas en Windows Server](#BKMK_msvsmon).

* Si desea obtener ayuda para asegurarse de la aplicación está configurada, implementa y ejecute correctamente en IIS para que puedan depurar, siga todos los pasos de este tema.

### <a name="update-browser-security-settings-on-windows-server"></a>Actualizar la configuración de seguridad del explorador en Windows Server

Si está habilitada la configuración de seguridad mejorada de Internet Explorer (está habilitado de forma predeterminada), debe agregar algunos dominios como sitios de confianza para que le permitirán descargar algunos de los componentes de servidor web. Agregar los sitios de confianza, vaya a **opciones de Internet > seguridad > sitios de confianza > sitios**. Agregue los dominios siguientes.

- Microsoft.com
- go.microsoft.com
- download.microsoft.com
- IIS.NET

Al descargar el software, puede obtener las solicitudes para conceder permiso para cargar varias secuencias de comandos del sitio web y recursos. Algunos de estos recursos no son necesarias, pero para simplificar el proceso, haga clic en **agregar** cuando se le solicite.

### <a name="install-aspnet-core-on-windows-server"></a>Instalar ASP.NET Core en Windows Server

1. Instalar el [hospedaje de .NET Core Windows Server](https://aka.ms/dotnetcore-2-windowshosting) agrupación en el sistema host. La agrupación instalará el tiempo de ejecución de .NET Core, biblioteca principal de .NET y el módulo de núcleo de ASP.NET. Para obtener instrucciones más detalladas, consulte [publicar en IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    > [!NOTE]
    > Si el sistema no tiene una conexión a Internet, obtenga e instale el *[Microsoft Visual C++ 2015 Redistributable](https://www.microsoft.com/download/details.aspx?id=53840)* antes de instalar el paquete de hospedaje de .NET Core Windows Server.

3. Reiniciar el sistema (o ejecutar **net stop era /y** seguido **del comando net start w3svc** desde un símbolo del sistema para recoger un cambio en la ruta de acceso del sistema).

## <a name="choose-a-deployment-option"></a>Elija una opción de implementación

Si necesita ayuda para implementar la aplicación en IIS, considere las siguientes opciones:

* Implementar mediante la creación de un archivo de configuración de publicación en IIS e importar la configuración de Visual Studio. En algunos escenarios, se trata de una forma rápida de implementar la aplicación. Cuando se crea el archivo de configuración de publicación, los permisos se configuran automáticamente en IIS.

* Implementar mediante la publicación en una carpeta local y copia el resultado por un método preferido en una carpeta de aplicación preparada en IIS.

## <a name="optional-deploy-using-a-publish-settings-file"></a>(Opcional) La implementación con un archivo de configuración de publicación

Puede usar esta opción crea un archivo de configuración de publicación y se importa en Visual Studio.

> [!NOTE]
> Este método de implementación utiliza Web Deploy. Si desea configurar Web Deploy manualmente en Visual Studio en lugar de importar la configuración, puede instalar Web implementar 3.6 en lugar de 3.6 de implementación Web para servidores de hospedaje. Sin embargo, si configura Web Deploy manualmente, debe asegurarse de que una carpeta de la aplicación en el servidor está configurada con los valores correctos y permisos (vea [sitio Web de ASP.NET configurar](#BKMK_deploy_asp_net)).

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Instalar y configurar Web Deploy para los servidores de hospedaje de Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Crear el archivo de configuración de publicación en IIS en Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importar la configuración de publicación en Visual Studio e implementar

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Después de que la aplicación se implementa correctamente, debe iniciarse automáticamente. Si la aplicación no se inicia desde Visual Studio, inicie la aplicación en IIS. Para ASP.NET Core, debe asegurarse de que el grupo de aplicaciones de campo para el **DefaultAppPool** está establecido en **sin código administrado**.

1. En el **configuración** cuadro de diálogo, Habilitar depuración haciendo clic en **siguiente**, elija un **depurar** configuración y, a continuación, elija **quitar archivos adicionales en destino** en el **Publicar archivo** opciones.

    > [!NOTE]
    > Si elige una configuración de lanzamiento, deshabilite la depuración en el *web.config* archivos al publicar.

1. Haga clic en **guardar** y, a continuación, volver a publicar la aplicación.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(Opcional) Implementar mediante la publicación en una carpeta local

Puede usar esta opción para implementar la aplicación si van a copiar la aplicación en IIS con Powershell, RoboCopy, o desea copiar manualmente los archivos.

### <a name="BKMK_deploy_asp_net"></a> Configurar el sitio Web de ASP.NET en el equipo de Windows Server

Si va a importar la configuración de publicación, puede omitir esta sección.

1. Abra el **Administrador de Internet Information Services (IIS)** y vaya a **Sitios**.

2. Haga clic con el botón secundario en el nodo **Sitio web predeterminado** y seleccione **Agregar aplicación**.

3. Establecer el **Alias** campo **MyASPApp** y el campo de grupo de aplicaciones a **sin código administrado**. Establecer el **ruta de acceso física** a **C:\Publish** (donde posteriormente implementará el proyecto ASP.NET).

4. Con el sitio seleccionado en el Administrador de IIS, elija **Editar permisos**y asegúrese de que ese IUSR, IIS_IUSRS o el usuario configurado para el grupo de aplicaciones es un usuario autorizado con permisos de lectura y ejecución.

    Si no ve uno de estos usuarios con acceso, vaya a través de los pasos necesarios para agregar IUSR como un usuario con derechos de lectura y ejecución.

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>(Opcional) Publique e implemente la aplicación al realizar la publicación en una carpeta local de Visual Studio

Si no usa Web Deploy, debe publicar e implementar la aplicación mediante el sistema de archivos u otras herramientas. Puede iniciar mediante la creación de un paquete mediante el sistema de archivos y, a continuación, implementar manualmente el paquete o usar otras herramientas, como XCopy, RoboCopy o PowerShell. En esta sección, se supone que va a copiar manualmente el paquete si no se utiliza Web Deploy.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="BKMK_msvsmon"></a> Descargue e instale las herramientas remotas en Windows Server

En este tutorial, estamos utilizando Visual Studio de 2017.

Si tiene problemas para abrir la página con la descarga del depurador remoto, consulte [desbloquear la descarga del archivo](../debugger/remote-debugging.md#unblock_msvsmon) para obtener ayuda.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
### <a name="BKMK_setup"></a> Configurar el depurador remoto en Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Si necesita agregar permisos para los usuarios adicionales, cambiar el modo de autenticación o número de puerto para el depurador remoto, consulte [configurar el depurador remoto](../debugger/remote-debugging.md#configure_msvsmon).

### <a name="BKMK_attach"></a> Adjuntar elementos a la aplicación ASP.NET desde el equipo de Visual Studio

1. En el equipo de Visual Studio, abra la solución que está intentando depurar (**MyASPApp** si está siguiendo los pasos descritos en este artículo).
2. En Visual Studio, haga clic en **Depurar > asociar al proceso** (Ctrl + Alt + P).

    > [!TIP]
    > En Visual Studio de 2017, puede volver a adjuntar al mismo proceso que ha asociado previamente a mediante el uso de **Depurar > volver a adjuntar al proceso...** (Mayús + Alt + P). 

3. Establezca el campo calificador en  **\<nombre del equipo remoto >: 4022**.
4. Haga clic en **Actualizar**.
    Debería ver que algunos procesos aparecen en la ventana **Procesos disponibles** .

    Si no ve todos los procesos, pruebe a usar la dirección IP en lugar del nombre del equipo remoto (el puerto es necesario). Puede usar `ipconfig` en una línea de comandos para obtener la dirección IPv4.

    Si desea utilizar el **buscar** botón, puede que necesite [abrir el puerto UDP 3702](#bkmk_openports) en el servidor.

5. Active  **Mostrar los procesos de todos los usuarios**.

6. Escriba la primera letra de un nombre de proceso para encontrar rápidamente *dotnet.exe* (para ASP.NET Core).
   
   Para una aplicación ASP.NET Core, el nombre del proceso anterior era *dnx.exe*.

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

