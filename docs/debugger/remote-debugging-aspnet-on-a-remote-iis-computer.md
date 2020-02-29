---
title: ASP.NET Core de depuración remota en un equipo remoto de IIS | Microsoft Docs
ms.custom: remotedebugging
ms.date: 05/21/2018
ms.topic: conceptual
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: f3741f9b510450dabfea5c1df4eec4b2e0868b26
ms.sourcegitcommit: 3d64bfb9bf85395357effe054db9a9afaa0be5ea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/29/2020
ms.locfileid: "78181151"
---
# <a name="remote-debug-aspnet-core-on-a-remote-iis-computer-in-visual-studio"></a>Depuración remota ASP.NET Core en un equipo remoto de IIS en Visual Studio

Para depurar una aplicación ASP.NET Core que se ha implementado en IIS, instale y ejecute las herramientas remotas en el equipo donde ha implementado la aplicación y, a continuación, conéctese a la aplicación en ejecución desde Visual Studio.

![Componentes del Depurador remoto](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

En esta guía se explica cómo instalar y configurar un ASP.NET Core de Visual Studio, cómo implementarlo en IIS y cómo adjuntar el depurador remoto desde Visual Studio. Para depurar de forma remota ASP.NET 4.5.2, consulte [depuración remota de ASP.net en un equipo con IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). También puede implementar y depurar en IIS con Azure. Por Azure App Service, puede implementar y depurar fácilmente en una instancia preconfigurada de IIS y el depurador remoto mediante el [Snapshot Debugger](../debugger/debug-live-azure-applications.md) o [adjuntando el depurador de explorador de servidores](../debugger/remote-debugging-azure.md).

## <a name="prerequisites"></a>Prerequisites

::: moniker range=">=vs-2019"
Visual Studio 2019 es necesario para seguir los pasos que se muestran en este artículo.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017 es necesario para seguir los pasos que se muestran en este artículo.
::: moniker-end

Estos procedimientos se han probado en estas configuraciones de servidor:
* Windows Server 2012 R2 e IIS 8
* Windows Server 2016 e IIS 10

## <a name="network-requirements"></a>Requisitos de red

No se admite la depuración entre dos equipos conectados a través de un proxy. No se recomienda la depuración a través de una conexión de alta latencia o de ancho de banda bajo, como acceso telefónico a Internet o a través de Internet a través de países, y puede producir un error o ser inaceptablemente lento. Para obtener una lista completa de los requisitos, consulte [requisitos](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="app-already-running-in-iis"></a>¿La aplicación ya se está ejecutando en IIS?

En este artículo se incluyen los pasos para configurar una configuración básica de IIS en Windows Server e implementar la aplicación desde Visual Studio. Estos pasos se incluyen para asegurarse de que el servidor tiene instalados los componentes necesarios, que la aplicación se puede ejecutar correctamente y que está listo para la depuración remota.

* Si la aplicación se ejecuta en IIS y solo desea descargar el depurador remoto e iniciar la depuración, vaya a [Descargar e instalar las herramientas remotas en Windows Server](#BKMK_msvsmon).

* Si desea obtener ayuda para asegurarse de que la aplicación está configurada, implementada y ejecutándose correctamente en IIS para que pueda depurar, siga todos los pasos de este tema.

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Crear la aplicación ASP.NET Core en el equipo de Visual Studio

1. Cree una aplicación web de ASP.NET Core. 

    ::: moniker range=">=vs-2019"
    En Visual Studio 2019, escriba **Ctrl + Q** para abrir el cuadro de búsqueda, escriba **ASP.net**, elija **plantillas**y, a continuación, elija **crear nuevo ASP.net Core aplicación web**. En el cuadro de diálogo que aparece, asigne al proyecto el nombre **MyASPApp**y, a continuación, elija **crear**. A continuación, elija **aplicación web (controlador de vista de modelo)** y, a continuación, elija **crear**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    En Visual Studio 2017, elija **archivo > nuevo > proyecto**y, a continuación, seleccione **Visual C# > Web > ASP.net Core aplicación web**. En la sección plantillas de ASP.NET Core, seleccione **aplicación web (Model-View-Controller)** . Asegúrese de que se ha seleccionado ASP.NET Core 2,1, que no está seleccionada la opción **Habilitar compatibilidad con Docker** y que la **autenticación** está establecida en **sin autenticación**. Asigne al proyecto el nombre **MyASPApp**.
    ::: moniker-end

4. Abra el archivo About.cshtml.cs y establezca un punto de interrupción en el método `OnGet` (en las plantillas anteriores, abra HomeController.cs en su lugar y establezca el punto de interrupción en el método `About()`).

## <a name="bkmk_configureIIS"></a>Instalar y configurar IIS en Windows Server

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Actualizar la configuración de seguridad del explorador en Windows Server

Si la opción Configuración de seguridad mejorada está habilitada en Internet Explorer (está habilitada de forma predeterminada), es posible que deba agregar algunos dominios como sitios de confianza para poder descargar algunos de los componentes de servidor Web. Para agregar sitios de confianza, vaya a **Opciones de Internet > seguridad > sitios de confianza > sitios**. Agregue los siguientes dominios.

- microsoft.com
- go.microsoft.com
- download.Microsoft.com
- iis.net

Al descargar el software, puede recibir solicitudes para conceder permiso para cargar varios scripts y recursos de sitios Web. Algunos de estos recursos no son necesarios, pero para simplificar el proceso, haga clic en **Agregar** cuando se le solicite.

## <a name="install-aspnet-core-on-windows-server"></a>Instalación de ASP.NET Core en Windows Server

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

1. Abra el explorador de Windows y cree una nueva carpeta, **C:\Publish**, donde implementará más adelante el proyecto ASP.net Core.

2. Si aún no está abierto, abra el **Administrador de Internet Information Services (IIS)** . (En el panel izquierdo de Administrador del servidor, seleccione **IIS**. Haga clic con el botón derecho en el servidor y seleccione **Administrador de Internet Information Services (IIS)** .)

3. En **conexiones** en el panel izquierdo, vaya a **sitios**.

4. Seleccione el **sitio web predeterminado**, elija **configuración básica**y establezca la **ruta de acceso física** en **C:\Publish**.

4. Haga clic con el botón secundario en el nodo **Sitio web predeterminado** y seleccione **Agregar aplicación**.

5. Establezca el campo **alias** en **MyASPApp**, acepte el grupo de aplicaciones predeterminado (**DefaultAppPool**) y establezca la **ruta de acceso física** en **C:\Publish**.

6. En **conexiones**, seleccione **grupos de aplicaciones**. Abra **DefaultAppPool** y establezca el campo Grupo de aplicaciones en **sin código administrado**.

7. Haga clic con el botón derecho en el nuevo sitio en el administrador de IIS, elija **Editar permisos**y asegúrese de que IUSR, IIS_IUSRS o el usuario configurado para el acceso a la aplicación web sea un usuario autorizado con derechos de ejecución de lectura &.

    Si no ve uno de estos usuarios con acceso, siga los pasos para agregar IUSR como usuario con derechos de lectura & ejecución.

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Publicar e implementar la aplicación mediante la publicación en una carpeta local desde Visual Studio

También puede publicar e implementar la aplicación con el sistema de archivos u otras herramientas.

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

1. En el equipo de Visual Studio, abra la solución que está intentando depurar (**MyASPApp** si está siguiendo todos los pasos de este artículo).
2. En Visual Studio, haga clic en **Depurar > asociar al proceso** (Ctrl + Alt + P).

    > [!TIP]
    > En Visual Studio 2017 y versiones posteriores, puede volver a asociar al mismo proceso que adjuntó anteriormente a mediante **Debug > volver a adjuntar al proceso...** (Mayús + Alt + P).

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

    * Seleccione **dotnet. exe**.

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

2. A continuación, elija **reglas de entrada > nueva regla > puerto**y, a continuación, haga clic en **siguiente**. (Para UDP 3702, seleccione **reglas de salida** en su lugar).

3. En **puertos locales específicos**, escriba el número de puerto y haga clic en **siguiente**.

4. Haga clic en **permitir la conexión**y en **siguiente**.

5. Seleccione uno o más tipos de red para habilitar para el puerto y haga clic en **siguiente**.

    Los tipos seleccionados deben incluir la red a la que está conectado el equipo remoto.
6. Agregue el nombre (por ejemplo, **IIS**, **Web deploy**o **msvsmon**) para la regla de entrada y haga clic en **Finalizar**.

    Debería ver la nueva regla en la lista Reglas de entrada o Reglas de salida.

    Si desea obtener más información acerca de cómo configurar el Firewall de Windows, consulte [configurar Firewall de Windows para la depuración remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Cree reglas adicionales para los demás puertos necesarios.
