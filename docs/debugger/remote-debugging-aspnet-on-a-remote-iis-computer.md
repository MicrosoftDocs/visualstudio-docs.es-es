---
title: Remoto depurar principales de ASP.NET en un equipo remoto de IIS | Documentos de Microsoft
ms.custom: remotedebugging
ms.date: 08/14/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: e4c0311f8e011b8cab3e189f309cd618a485bd71
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="remote-debug-aspnet-core-on-a-remote-iis-computer-in-visual-studio-2017"></a>Núcleo de ASP.NET de depuración remota en un equipo IIS remoto en Visual Studio de 2017
Para depurar una aplicación ASP.NET que se ha implementado en IIS, instalar y ejecutar las herramientas remotas en el equipo donde se implementa la aplicación y, a continuación, adjunte a su aplicación en ejecución desde Visual Studio.

![Los componentes del depurador remoto](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

Esta guía explica cómo instalar y configurar un núcleo de ASP.NET de Visual Studio de 2017, implementarla en IIS y asociar al depurador remoto de Visual Studio. Realizar la depuración remota ASP.NET 4.5.2, consulte [ASP.NET de depuración remota en un equipo con IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). También puede implementar y depurar en IIS con Azure. Para el servicio de aplicación de Azure, facilidad puede implementar y depurar en una instancia preconfigurada de IIS y el depurador remoto mediante el [depurador de instantánea](../debugger/debug-live-azure-applications.md) o [para asociar el depurador del explorador de servidores](../debugger/remote-debugging-azure.md).

Estos procedimientos se han probado en estas configuraciones de servidor:
* Windows Server 2012 R2 y IIS 8
* Windows Server 2016 y IIS 10

## <a name="requirements"></a>Requisitos

No se admite la depuración entre dos equipos conectados a través de un servidor proxy. Depuración mediante una conexión de poco ancho de banda, como acceso telefónico a Internet, o una latencia alta o a través de Internet a través de países no se recomienda y puede ser un error o inaceptablemente bajo. Para obtener una lista completa de requisitos, consulte [requisitos](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="create-the-aspnet-core-application-on-the-visual-studio-2017-computer"></a>Crear la aplicación de ASP.NET Core en el equipo de Visual Studio de 2017 

1. Cree una nueva aplicación de ASP.NET Core. (**Archivo > Nuevo > proyecto**, a continuación, seleccione **Visual C# > Web > aplicación Web de ASP.NET Core**).

    En el **ASP.NET Core** sección plantillas, seleccione **aplicación Web**.

2. Asegúrese de que **ASP.NET Core 2.0** está seleccionada, que **habilitar la compatibilidad con Docker** es **no** seleccionada y que **autenticación** está establecido en **Sin autenticación**.

3. Denomine el proyecto **MyASPApp** y haga clic en **Aceptar** para crear la nueva solución.

4. Abra el archivo About.cshtml.cs y establecer un punto de interrupción en la `OnGet` (método) (en las plantillas anteriores, abra HomeController.cs en su lugar y establecer el punto de interrupción en el `About()` método).

## <a name="bkmk_configureIIS"></a> Instalar y configurar IIS en Windows Server

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Actualizar la configuración de seguridad del explorador en Windows Server

Según la configuración de seguridad, puede ahorrar tiempo para agregar los siguientes sitios de confianza en el explorador, por lo que puede descargar fácilmente el software descrito en este tutorial. Puede ser necesario tener acceso a estos sitios:

- Microsoft.com
- go.microsoft.com
- download.microsoft.com
- visualstudio.com

Si está usando Internet Explorer, puede agregar los sitios de confianza, vaya a **opciones de Internet > seguridad > sitios de confianza > sitios**. Estos pasos son diferentes para otros exploradores. (Si tiene que descargar una versión anterior del depurador remoto de my.visualstudio.com, algunos sitios de confianza adicionales son necesarios para iniciar sesión).

Al descargar el software, puede obtener las solicitudes para conceder permiso para cargar varias secuencias de comandos del sitio web y recursos. En la mayoría de los casos, estos recursos adicionales no son necesarios para instalar el software.

## <a name="install-aspnet-core-on-windows-server"></a>Instalar ASP.NET Core en Windows Server

1. Instalar el [hospedaje de .NET Core Windows Server](https://aka.ms/dotnetcore-2-windowshosting) agrupación en el sistema host. El tiempo de ejecución de .NET Core, biblioteca principal de .NET y el módulo de núcleo de ASP.NET, instala la agrupación. Para obtener instrucciones más detalladas, consulte [publicar en IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    > [!NOTE]
    > Si el sistema no tiene una conexión a Internet, obtenga e instale el *[Microsoft Visual C++ 2015 Redistributable](https://www.microsoft.com/download/details.aspx?id=53840)* antes de instalar el paquete de hospedaje de .NET Core Windows Server.

3. Reiniciar el sistema (o ejecutar **net stop era /y** seguido **del comando net start w3svc** desde un símbolo del sistema para recoger un cambio en la ruta de acceso del sistema).

## <a name="BKMK_install_webdeploy"></a> (Opcional) Instale WebDeploy 3.6 en Windows Server

[!INCLUDE [remote-debugger-install-web-deploy](../debugger/includes/remote-debugger-install-web-deploy.md)]

## <a name="BKMK_deploy_asp_net"></a> Configurar el sitio Web de ASP.NET en el equipo de Windows Server

1. Abra el Explorador de Windows y cree una nueva carpeta, **C:\Publish**, donde va a implementar el proyecto ASP.NET más adelante.

2. Abra la **de Internet Information Services (IIS) Manager**. (En el panel izquierdo del administrador del servidor, seleccione **IIS**. Haga clic en el servidor y seleccione **Internet Information Services (IIS) Manager**.)

3. En **conexiones** en el panel izquierdo, vaya a **sitios**.

4. Seleccione el **sitio Web predeterminado**, elija **configuración básica**y establezca el **ruta de acceso física** a **C:\Publish**.

4. Haga clic con el botón secundario en el nodo **Sitio web predeterminado** y seleccione **Agregar aplicación**.

5. Establecer el **Alias** campo **MyASPApp**, acepte el valor predeterminado de grupo de aplicaciones (**DefaultAppPool**) y establezca el **ruta de acceso física** a  **C:\Publish**.

6. En **conexiones**, seleccione **grupos de aplicaciones**. Abra **DefaultAppPool** y establezca el campo de grupo de aplicaciones en **sin código administrado**.

7. Haga clic en el nuevo sitio en el Administrador de IIS, elija **Editar permisos**y asegúrese de que ese IUSR, IIS_IUSRS o el usuario configurado para el acceso a la aplicación web es un usuario autorizado con permisos de lectura y ejecución.

    Si no ve uno de estos usuarios con acceso, vaya a través de los pasos necesarios para agregar IUSR como un usuario con derechos de lectura y ejecución.

## <a name="bkmk_webdeploy"></a> (Opcional) Publique e implemente la aplicación mediante Web Deploy desde Visual Studio

[!INCLUDE [remote-debugger-deploy-app-web-deploy](../debugger/includes/remote-debugger-deploy-app-web-deploy.md)]

## <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>(Opcional) Publique e implemente la aplicación al realizar la publicación en una carpeta local de Visual Studio

También puede publicar e implementar la aplicación mediante el sistema de archivos u otras herramientas.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="BKMK_msvsmon"></a> Descargue e instale las herramientas remotas en Windows Server

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> En algunos casos, puede ser más eficaz para ejecutar al depurador remoto desde un recurso compartido de archivos. Para obtener más información, consulte [ejecutar el depurador remoto desde un recurso compartido de archivos](../debugger/remote-debugging.md#fileshare_msvsmon).
  
## <a name="BKMK_setup"></a> Configurar el depurador remoto en Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Si necesita agregar permisos para los usuarios adicionales, cambiar el modo de autenticación o número de puerto para el depurador remoto, consulte [configurar el depurador remoto](../debugger/remote-debugging.md#configure_msvsmon).

Para obtener información acerca de cómo ejecutar el depurador remoto como un servicio, consulte [ejecutar el depurador remoto como un servicio](../debugger/remote-debugging.md#bkmk_configureService).

## <a name="BKMK_attach"></a> Adjuntar elementos a la aplicación ASP.NET desde el equipo de Visual Studio

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

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg_attachtoprocess_aspnetcore.png "RemoteDBG_AttachToProcess")

7. Haga clic en **Adjuntar**.

8. Abra el sitio web del equipo remoto. En un explorador, vaya a **http://\<nombre del equipo remoto >**.
    
    Debería ver la página web de ASP.NET.

9. En la aplicación ASP.NET en ejecución, haga clic en el vínculo a la **sobre** página.

    Se alcanzará el punto de interrupción en Visual Studio.

## <a name="bkmk_openports"></a> Solución de problemas: Abra los puertos necesarios en Windows Server

En la mayoría de las instalaciones, se abren los puertos necesarios por la instalación de ASP.NET y el depurador remoto. Sin embargo, debe comprobar que los puertos estén abiertos.

> [!NOTE]
> En una máquina virtual de Azure, debe abrir puertos a través de la [grupo de seguridad de red](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80). 

Puertos necesarios:

- 80 - necesarias para IIS
- 4022 - necesarios para la depuración remota de Visual Studio de 2017 (vea [asignaciones de puerto de depurador remoto](../debugger/remote-debugger-port-assignments.md) para obtener información detallada.
- 8172 - (opcional) es necesario para que Web Deploy implementar la aplicación desde Visual Studio.
- UDP 3702 - puerto de detección (opcional) permite la **buscar** botón al adjuntar el depurador remoto en Visual Studio.

1. Para abrir un puerto de servidor de Windows, abra la **iniciar** menú, busque **Firewall de Windows con seguridad avanzada**.

2. A continuación, elija **reglas de entrada > nueva regla > puerto**y, a continuación, haga clic en **siguiente**. (Para UDP 3702, elija **reglas de salida** en su lugar.)

3. En **puertos locales específicos**, escriba el número de puerto, haga clic en **siguiente**.

4. Haga clic en **permitir la conexión**, haga clic en **siguiente**.

5. Seleccione uno o más tipos de red desea habilitar para el puerto y haga clic en **siguiente**.

    Los tipos seleccionados deben incluir la red a la que está conectado el equipo remoto.
6. Agregue el nombre (por ejemplo, **IIS**, **Web Deploy**, o **msvsmon**) para la regla de entrada y haga clic en **finalizar**.

    Debería ver la nueva regla en la lista de reglas de entrada o las reglas de salida.

    Si desea obtener más información acerca de cómo configurar Firewall de Windows, vea [configurar Firewall de Windows para la depuración remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Cree reglas adicionales para los otros puertos necesarios.
