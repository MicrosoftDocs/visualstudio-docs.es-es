---
title: Depuración remota de ASP.NET Core en IIS y Azure | Microsoft Docs
ms.custom: remotedebugging
ms.date: 05/21/2018
ms.topic: conceptual
ms.assetid: a6c04b53-d1b9-4552-a8fd-3ed6f4902ce6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
- dotnetcore
- azure
ms.openlocfilehash: 1658e8df9950ed7b9be060663204511a09d8c626
ms.sourcegitcommit: 5a65ca6688a2ebb36564657d2d73c4b4f2d15c34
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "53839101"
---
# <a name="remote-debug-aspnet-core-on-iis-in-azure-in-visual-studio-2017"></a>Depuración remota de ASP.NET Core en IIS en Azure en Visual Studio 2017

Esta guía explica cómo configurar y configurar una aplicación ASP.NET Core de Visual Studio 2017, implementarla en IIS con Azure y asociar al depurador remoto de Visual Studio.

La manera recomendada para la depuración remota en Azure depende de su escenario:

* Para depurar ASP.NET Core en Azure App Service, consulte [depurar Azure apps mediante el depurador de instantáneas](../debugger/debug-live-azure-applications.md). Este es el método recomendado.
* Para depurar ASP.NET Core en Azure App Service mediante las características de depuración más tradicionales, siga los pasos de este tema (vea la sección [depuración remota en Azure App Service](#remote_debug_azure_app_service)).

    En este escenario, debe implementar la aplicación desde Visual Studio en Azure, pero no es necesario instalar manualmente o configurar IIS o el depurador remoto (estos componentes se representan con líneas de puntos), tal como se muestra en la siguiente ilustración.

    ![Componentes del depurador remoto](../debugger/media/remote-debugger-azure-app-service.png "Remote_debugger_components")

* Para depurar IIS en una máquina virtual de Azure, siga los pasos descritos en este tema (vea la sección [de depuración remota en una máquina virtual de Azure](#remote_debug_azure_vm)). Esto le permite usar una configuración personalizada de IIS, pero los pasos de instalación e implementación son más complicados.

    Para una máquina virtual de Azure, debe implementar la aplicación desde Visual Studio en Azure y también debe instalar manualmente el rol de IIS y el depurador remoto, tal como se muestra en la siguiente ilustración.

    ![Componentes del depurador remoto](../debugger/media/remote-debugger-azure-vm.png "Remote_debugger_components")

* Para depurar ASP.NET Core en Azure Service Fabric, consulte [depurar una aplicación de Service Fabric remota](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application).

> [!WARNING]
> No olvide eliminar los recursos de Azure que cree cuando haya completado los pasos de este tutorial. De este modo que puede evitar gastos innecesarios.


### <a name="requirements"></a>Requisitos

No se admite la depuración entre dos equipos conectados a través de un servidor proxy. Depuración mediante una conexión de ancho de banda bajo, por ejemplo, acceso telefónico a Internet, o una latencia alta o a través de Internet entre países no se recomienda y puede ser un error o inaceptablemente bajo. Para obtener una lista completa de requisitos, consulte [requisitos](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="create-the-aspnet-core-application-on-the-visual-studio-2017-computer"></a>Crear la aplicación de ASP.NET Core en el equipo de Visual Studio 2017 

1. Cree una nueva aplicación de ASP.NET Core. (Elija **archivo > Nuevo > proyecto**, a continuación, seleccione **Visual C# > Web > aplicación Web ASP.NET Core**).

    En el **ASP.NET Core** sección plantillas, seleccione **aplicación Web**.

2. Asegúrese de que **ASP.NET Core 2.0** está seleccionada, que **habilitar la compatibilidad con Docker** es **no** seleccionada y que **autenticación** está establecido en **Sin autenticación**.

3. Denomine el proyecto **MyASPApp** y haga clic en **Aceptar** para crear la nueva solución.

4. Abra el archivo About.cshtml.cs y establecer un punto de interrupción en el `OnGet` método (en las plantillas anteriores, abra HomeController.cs en su lugar y establezca el punto de interrupción en el `About()` método).

## <a name="remote_debug_azure_app_service"></a> Depuración remota de ASP.NET Core en Azure App Service

Desde Visual Studio, puede publicar rápidamente y depurar la aplicación a una instancia totalmente aprovisionada de IIS. Sin embargo, la configuración de IIS está predefinida y no puede personalizarlo. Para obtener instrucciones detalladas, consulte [implementar una aplicación web ASP.NET Core en Azure con Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). (Si necesita la capacidad de personalizar IIS, pruebe la depuración un [Azure VM](#remote_debug_azure_vm).) 

#### <a name="to-deploy-the-app-and-remote-debug-using-server-explorer"></a>Para implementar la aplicación y la depuración remota mediante el Explorador de servidores

1. En Visual Studio, haga clic en el nodo del proyecto y elija **publicar**.

    Si previamente ha configurado algún perfil de publicación, aparece el panel **Publicar**. Haga clic en **nuevo perfil**.

1. Elija **Azure App Service** desde el **publicar** cuadro de diálogo, seleccione **crear nuevo**y siga las indicaciones para publicar.

    Para obtener instrucciones detalladas, vea [Publicar una aplicación de ASP.NET Core en Azure con Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

    ![Publicación en Azure App Service](../debugger/media/remotedbg_azure_app_service_profile.png)

1. Abra **Explorador de servidores** (**vista** > **Explorador de servidores**), haga doble clic en la instancia de App Service y elija **adjuntar depurador**.

1. En la aplicación ASP.NET en ejecución, haga clic en el vínculo a la **sobre** página.

    Se alcanzará el punto de interrupción en Visual Studio.

    Ya está. El resto de los pasos descritos en este tema se aplican a la depuración remota en una máquina virtual de Azure.

## <a name="remote_debug_azure_vm"></a> Depuración remota de ASP.NET Core en una máquina virtual de Azure

Puede crear una máquina virtual de Azure para Windows Server y, a continuación, instalar y configurar IIS y los demás componentes de software necesarias. Esto requiere más tiempo que la implementación en Azure App Service y requiere que siga los pasos restantes de este tutorial.

En primer lugar, siga los pasos descritos en [instalación y ejecución de IIS](/azure/virtual-machines/windows/quick-create-portal).

Al abrir el puerto 80 en el grupo de seguridad de red, abrir el puerto 4022 para el depurador remoto. De este modo, no tendrá que abrirla de nuevo más tarde.

### <a name="app-already-running-in-iis-on-the-azure-vm"></a>¿Aplicación ya que se ejecuta en IIS en la máquina virtual de Azure?

En este artículo incluye pasos sobre cómo configurar una configuración básica de IIS en Windows server y la implementación de la aplicación desde Visual Studio. Estos pasos se incluyen para asegurarse de que el servidor tiene los componentes necesarios instalados, que puede ejecutar correctamente la aplicación y que está listo para la depuración remota.

* Si la aplicación se ejecuta en IIS y simplemente desea descargar el depurador remoto e iniciar la depuración, vaya a [descargar e instalar las herramientas remotas en Windows Server](#BKMK_msvsmon).

* Si desea obtener ayuda para asegurarse de que la aplicación se ha configurado, implementado y que se ejecutan correctamente en IIS para que pueda Depurar, siga todos los pasos de este tema.

### <a name="update-browser-security-settings-on-windows-server"></a>Actualizar configuración de seguridad del explorador en Windows Server

Si está habilitada la configuración de seguridad mejorada de Internet Explorer (está habilitado de forma predeterminada), es posible que deba agregar algunos dominios como sitios de confianza para que pueda descargar algunos de los componentes de servidor web. Agregar los sitios de confianza, vaya a **opciones de Internet > seguridad > sitios de confianza > sitios**. Agregue los siguientes dominios.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

Al descargar el software, obtendrá las solicitudes para conceder permiso para cargar varios scripts de sitios web y recursos. Algunos de estos recursos no son necesarias, pero para simplificar el proceso, haga clic en **agregar** cuando se le solicite.

### <a name="install-aspnet-core-on-windows-server"></a>Instalación de ASP.NET Core en Windows Server

1. Instale el [lote de hospedaje .NET Core Windows Server](https://aka.ms/dotnetcore-2-windowshosting) en el sistema host. El lote instala .NET Core Runtime, .NET Core Library y el módulo ASP.NET Core. Para obtener más instrucciones, consulte [publicar en IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    > [!NOTE]
    > Si el sistema no tiene conexión a Internet, obtenga e instale *[Microsoft Visual C++ 2015 Redistributable](https://www.microsoft.com/download/details.aspx?id=53840)* antes de instalar el lote de hospedaje .NET Core Windows Server.

3. Reinicie el sistema (o ejecute **net stop was /y** seguido de **net start w3svc** desde un símbolo del sistema para obtener un cambio en la ruta de acceso del sistema).

## <a name="choose-a-deployment-option"></a>Elija una opción de implementación

Si necesita ayuda para implementar la aplicación en IIS, considere las siguientes opciones:

* Implementar mediante la creación de un archivo de configuración de publicación en IIS e importar la configuración en Visual Studio. En algunos escenarios, se trata de una forma rápida de implementar la aplicación. Cuando se crea el archivo de configuración de publicación, los permisos se configuran automáticamente en IIS.

* Implementar mediante la publicación en una carpeta local y copiar el resultado por un método preferido para una carpeta de aplicación preparada en IIS.

## <a name="optional-deploy-using-a-publish-settings-file"></a>(Opcional) Implementar mediante un archivo de configuración de publicación

Puede usar esta opción crea un archivo de configuración de publicación y se importa en Visual Studio.

> [!NOTE]
> Este método de implementación utiliza Web Deploy. Si desea configurar Web Deploy manualmente en Visual Studio en lugar de importar la configuración, puede instalar 3.6 de implementación Web en lugar de 3.6 de implementación Web para servidores de hospedaje. Sin embargo, si configura Web Deploy manualmente, deberá asegurarse de que una carpeta de aplicación en el servidor está configurada con los valores correctos y permisos (consulte [configurar sitio Web de ASP.NET](#BKMK_deploy_asp_net)).

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Instalar y configurar Web Deploy para servidores de hospedaje en Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Crear el archivo de configuración de publicación en IIS en Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importar la configuración de publicación a Visual Studio e implementar

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Después de que se implemente la aplicación correctamente, debería iniciarse automáticamente. Si la aplicación no se inicia desde Visual Studio, inicie la aplicación en IIS. Para ASP.NET Core, deberá asegurarse de que el campo Grupo de aplicaciones para el **DefaultAppPool** está establecido en **Sin código administrado**.

1. En el **configuración** cuadro de diálogo, habilitar la depuración haciendo **siguiente**, elija un **depurar** configuración y, a continuación, elija **quitar archivos adicionales en destino** bajo el **Publicar archivo** opciones.

    > [!NOTE]
    > Si elige una configuración de lanzamiento, deshabilite la depuración en el *web.config* archivo al publicar.

1. Haga clic en **guardar** y, a continuación, volver a publicar la aplicación.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(Opcional) Implementar mediante la publicación en una carpeta local

Puede usar esta opción para implementar la aplicación si van a copiar la aplicación en IIS mediante Powershell, RoboCopy, o desea copiar manualmente los archivos.

### <a name="BKMK_deploy_asp_net"></a> Configurar el sitio Web de ASP.NET en el equipo de Windows Server

Si va a importar la configuración de publicación, puede omitir esta sección.

1. Abra el **Administrador de Internet Information Services (IIS)** y vaya a **Sitios**.

2. Haga clic con el botón secundario en el nodo **Sitio web predeterminado** y seleccione **Agregar aplicación**.

3. Establecer el **Alias** campo **MyASPApp** y el campo de grupo de aplicaciones a **sin código administrado**. Establecer el **ruta de acceso física** a **C:\Publish** (donde posteriormente implementará el proyecto ASP.NET).

4. Con el sitio seleccionado en el Administrador de IIS, elija **Editar permisos**y asegúrese de que ese IUSR, IIS_IUSRS o el usuario configurado para el grupo de aplicaciones es un usuario autorizado con derechos de lectura y ejecución.

    Si no ve uno de estos usuarios con acceso, siga los pasos para agregar IUSR como un usuario con derechos de lectura y ejecución.

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>(Opcional) Publicar e implementar la aplicación mediante la publicación en una carpeta local desde Visual Studio

Si no usa Web Deploy, debe publicar y volver a implementar la aplicación con el sistema de archivos u otras herramientas. Puede empezar creando un paquete con el sistema de archivos y, a continuación, implementar manualmente el paquete o usar otras herramientas, como XCopy, RoboCopy o PowerShell. En esta sección, se supone que va a copiar manualmente el paquete si no usa Web Deploy.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="BKMK_msvsmon"></a> Descargue e instale las herramientas remotas en Windows Server

En este tutorial, estamos usando Visual Studio 2017.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
### <a name="BKMK_setup"></a> Establecimiento del depurador remoto en Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Si necesita agregar permisos para usuarios adicionales, cambiar el modo de autenticación, o número de puerto para el depurador remoto, consulte [configurar el depurador remoto](../debugger/remote-debugging.md#configure_msvsmon).

### <a name="BKMK_attach"></a> Adjuntar elementos a la aplicación ASP.NET desde el equipo de Visual Studio

1. En el equipo de Visual Studio, abra la solución que está intentando depurar (**MyASPApp** si está siguiendo los pasos descritos en este artículo).
2. En Visual Studio, haga clic en **Depurar > asociar al proceso** (Ctrl + Alt + P).

    > [!TIP]
    > En Visual Studio 2017, puede volver a adjuntar al mismo proceso adjuntado previamente, utilizando **Depurar > adjuntar al proceso...** Mayús+Alt+P 

3. Establezca el campo Calificador en **\<nombre de equipo remoto>:4022**.
4. Haga clic en **Actualizar**.
    Debería ver que algunos procesos aparecen en la ventana **Procesos disponibles** .

    Si no ve todos los procesos, pruebe a usar la dirección IP en lugar del nombre del equipo remoto (el puerto es necesario). Puede usar `ipconfig` en una línea de comandos para obtener la dirección IPv4.

    Si desea usar el **buscar** botón, es posible que deba [abrir el puerto UDP 3702](#bkmk_openports) en el servidor.

5. Active  **Mostrar los procesos de todos los usuarios**.

6. Escriba la primera letra de un nombre de proceso para encontrar rápidamente *dotnet.exe* (para ASP.NET Core).
   
   Para una aplicación ASP.NET Core, el nombre de proceso anterior era *dnx.exe*.

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg_attachtoprocess_aspnetcore.png "RemoteDBG_AttachToProcess")

7. Haga clic en **Adjuntar**.

8. Abra el sitio web del equipo remoto. En un explorador, vaya a **http://\<nombre del equipo remoto>**.
    
    Debería ver la página web de ASP.NET.
9. En la aplicación ASP.NET en ejecución, haga clic en el vínculo a la **sobre** página.

    Se alcanzará el punto de interrupción en Visual Studio.

### <a name="bkmk_openports">Solución de problemas</a> Abra los puertos necesarios en Windows Server

En la mayoría de las instalaciones, se abren los puertos requeridos por la instalación de ASP.NET y el depurador remoto. Sin embargo, si está solucionando problemas de implementación y la aplicación se hospeda detrás de un firewall, es posible que deba comprobar que están abiertos los puertos correctos.

En una máquina virtual de Azure, debe abrir los puertos a través de la [grupo de seguridad de red](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80-for-web-traffic). 

Puertos necesarios:

- 80 - necesarias para IIS
- 4022 - necesarios para la depuración remota desde Visual Studio 2017 (consulte [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md) para obtener más información).
- UDP 3702 - puerto de detección (opcional) permite la **buscar** botón al asociar el depurador remoto en Visual Studio.

Además, ya se deben abrir estos puertos mediante la instalación de ASP.NET:
- 8172: (opcional) necesario para que Web Deploy implementar la aplicación desde Visual Studio
