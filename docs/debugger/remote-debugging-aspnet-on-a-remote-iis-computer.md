---
title: Depurar ASP.NET núcleo remoto en un equipo IIS remoto ? Microsoft Docs
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
ms.openlocfilehash: b33ead969456935dab54c042ba4fbaf1f5ff44f4
ms.sourcegitcommit: cc58ca7ceae783b972ca25af69f17c9f92a29fc2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/15/2020
ms.locfileid: "81385479"
---
# <a name="remote-debug-aspnet-core-on-a-remote-iis-computer-in-visual-studio"></a>Depuración remota ASP.NET núcleo en un equipo IIS remoto en Visual Studio

Para depurar una aplicación ASP.NET Core que se ha implementado en IIS, instale y ejecute las herramientas remotas en el equipo donde implementó la aplicación y, a continuación, adjúntela a la aplicación en ejecución desde Visual Studio.

![Componentes del depurador remoto](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

Esta guía explica cómo configurar y configurar Visual Studio ASP.NET Core, implementarlo en IIS y adjuntar el depurador remoto desde Visual Studio. Para depurar de forma remota ASP.NET 4.5.2, vea [ASP.NET de depuración remota en un equipo IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). También puede implementar y depurar en IIS mediante Azure.You can also deploy and debug on IIS using Azure. Para Azure App Service, puede implementar y depurar fácilmente en una instancia preconfigurada de IIS y el depurador remoto mediante el depurador de [instantáneas](../debugger/debug-live-azure-applications.md) o [adjuntando el depurador desde el Explorador](../debugger/remote-debugging-azure.md)de servidores.

## <a name="prerequisites"></a>Prerrequisitos

::: moniker range=">=vs-2019"
Visual Studio 2019 es necesario seguir los pasos que se muestran en este artículo.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017 es necesario seguir los pasos que se muestran en este artículo.
::: moniker-end

Estos procedimientos se han probado en estas configuraciones del servidor:
* Windows Server 2012 R2 e IIS 8
* Windows Server 2016 e IIS 10

## <a name="network-requirements"></a>Requisitos de red

No se admite la depuración entre dos equipos conectados a través de un proxy. No se recomienda depurar a través de una conexión de alta latencia o de ancho de banda bajo, como Internet de acceso telefónico o a través de Internet entre países, y puede fallar o ser inaceptablemente lento. Para obtener una lista completa de los requisitos, consulte [Requisitos](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="app-already-running-in-iis"></a>¿La aplicación ya se está ejecutando en IIS?

En este artículo se incluyen los pasos para configurar una configuración básica de IIS en el servidor de Windows e implementar la aplicación desde Visual Studio. Estos pasos se incluyen para asegurarse de que el servidor tiene los componentes necesarios instalados, que la aplicación se puede ejecutar correctamente y que está listo para depurar de forma remota.

* Si la aplicación se ejecuta en IIS y solo desea descargar el depurador remoto e iniciar la depuración, vaya a [Descargar e instalar las herramientas remotas en Windows Server](#BKMK_msvsmon).

* Si desea ayuda para asegurarse de que la aplicación está configurada, implementada y ejecutándose correctamente en IIS para que pueda depurar, siga todos los pasos de este tema.

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Cree la aplicación ASP.NET Core en el equipo de Visual Studio

1. Cree una aplicación web de ASP.NET Core. 

    ::: moniker range=">=vs-2019"
    En Visual Studio 2019, escriba **Ctrl + Q** para abrir el cuadro de búsqueda, escriba **asp.net**, elija **Plantillas**y, a continuación, elija Crear nueva aplicación web **ASP.NET principal**. En el cuadro de diálogo que aparece, asigne al proyecto el nombre **MyASPApp**y, a continuación, elija **Create .** A continuación, elija **Web Application (Model-View-Controller)** y, a continuación, elija **Create**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    En Visual Studio 2017, elija **Archivo > Nuevo > proyecto**y, a continuación, seleccione Visual **C-> Web > ASP.NET aplicación web principal**. En la sección Plantillas ASP.NET Core, seleccione **Aplicación web (Model-View-Controller).** Asegúrese de que ASP.NET Core 2.1 está seleccionado, que **Habilitar compatibilidad con Docker** no está seleccionada y que **Autenticación** está establecida en **Sin autenticación**. Asigne al proyecto el nombre **MyASPApp**.
    ::: moniker-end

4. Abra el archivo About.cshtml.cs y establezca `OnGet` un punto de interrupción en el método `About()` (en plantillas anteriores, abra HomeController.cs en su lugar y establezca el punto de interrupción en el método).

## <a name="install-and-configure-iis-on-windows-server"></a><a name="bkmk_configureIIS"></a>Instalar y configurar IIS en Windows Server

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Actualizar la configuración de seguridad del explorador en Windows Server

Si la configuración de seguridad mejorada está habilitada en Internet Explorer (está habilitada de forma predeterminada), es posible que deba agregar algunos dominios como sitios de confianza para permitirle descargar algunos de los componentes del servidor web. Agregue los sitios de confianza yendo a Opciones de **Internet > Seguridad > Sitios de > de confianza**. Agregue los siguientes dominios.

- microsoft.com
- go.microsoft.com
- download.Microsoft.com
- iis.net

Al descargar el software, puede obtener solicitudes para conceder permiso para cargar varios scripts y recursos de sitios web. Algunos de estos recursos no son necesarios, pero para simplificar el proceso, haga clic en **Agregar** cuando se le solicite.

## <a name="install-aspnet-core-on-windows-server"></a>Instalar ASP.NET Core en Windows Server

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

1. Abra el Explorador de Windows y cree una nueva carpeta, **C:-Publicar**, donde más adelante implementará el proyecto ASP.NET Core.

2. Si aún no está abierto, abra el Administrador de **Internet Information Services (IIS).** (En el panel izquierdo del Administrador del servidor, seleccione **IIS**. Haga clic con el botón derecho en el servidor y seleccione Administrador de **Internet Information Services (IIS).)**

3. En **Conexiones** en el panel izquierdo, vaya a **Sitios**.

4. Seleccione el **sitio Web predeterminado**, elija configuración **básica**y establezca la ruta de **acceso física** en **C:-Publicar**.

4. Haga clic con el botón secundario en el nodo **Sitio web predeterminado** y seleccione **Agregar aplicación**.

5. Establezca el campo **Alias** en **MyASPApp**, acepte el grupo de aplicaciones predeterminado (**DefaultAppPool**) y establezca la **ruta de acceso física** en **C:-Publicar**.

6. En **Conexiones**, seleccione **Grupos de aplicaciones**. Abra **DefaultAppPool** y establezca el campo Grupo de aplicaciones en **Sin código administrado**.

7. Haga clic con el botón secundario en el nuevo sitio en el Administrador de IIS, elija **Editar permisos**y asegúrese de que IUSR, IIS_IUSRS o el usuario configurado para el acceso a la aplicación web es un usuario autorizado con derechos de lectura & ejecución.

    Si no ve uno de estos usuarios con acceso, siga los pasos para agregar IUSR como usuario con derechos de & Ejecutar.

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Publicar e implementar la aplicación mediante la publicación en una carpeta local desde Visual Studio

También puede publicar e implementar la aplicación mediante el sistema de archivos u otras herramientas.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="download-and-install-the-remote-tools-on-windows-server"></a><a name="BKMK_msvsmon"></a>Descargar e instalar las herramientas remotas en Windows Server

Descargue la versión de las herramientas remotas que coincida con su versión de Visual Studio.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="set-up-the-remote-debugger-on-windows-server"></a><a name="BKMK_setup"></a> Establecimiento del depurador remoto en Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Si necesita agregar permisos para usuarios adicionales, cambiar el modo de autenticación o el número de puerto para el depurador remoto, consulte [Configurar el depurador remoto](../debugger/remote-debugging.md#configure_msvsmon).

Para obtener información sobre cómo ejecutar el depurador remoto como un servicio, vea [Ejecutar el depurador remoto como un servicio.](../debugger/remote-debugging.md#bkmk_configureService)

## <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a><a name="BKMK_attach"></a>Adjuntar a la aplicación ASP.NET desde el equipo de Visual Studio

1. En el equipo de Visual Studio, abra la solución que está intentando depurar (**MyASPApp** si está siguiendo todos los pasos de este artículo).
2. En Visual Studio, haga clic en **Depurar > Adjuntar al proceso** (Ctrl + Alt + P).

    > [!TIP]
    > En Visual Studio 2017 y versiones posteriores, puede volver a adjuntar al mismo proceso al que se asentó anteriormente mediante **Depurar > Volver a adjuntar al proceso...** (Mayús + Alt + P).

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

    * Si usa el modelo de hospedaje en la [aplicación en](/aspnet/core/host-and-deploy/aspnet-core-module?view=aspnetcore-3.1#hosting-models) IIS, seleccione el proceso **w3wp.exe** correcto. A partir de .NET Core 3, este es el valor predeterminado.

    * De lo contrario, seleccione el proceso **dotnet.exe.** (Este es el modelo de hospedaje fuera de proceso.)

    Si tiene varios procesos que muestran *w3wp.exe* o *dotnet.exe*, compruebe la columna **Nombre de usuario.** En algunos escenarios, la columna **Nombre** de usuario muestra el nombre del grupo de aplicaciones, como **IIS APPPOOL-DefaultAppPool**. Si ve el grupo de aplicaciones, pero no es único, cree un nuevo grupo de aplicaciones con nombre para la instancia de aplicación que desea depurar y, a continuación, puede encontrarlo fácilmente en la columna **Nombre** de usuario.

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

## <a name="troubleshooting-open-required-ports-on-windows-server"></a><a name="bkmk_openports"></a> Solución de problemas Abra los puertos necesarios en Windows Server

En la mayoría de las configuraciones, los puertos necesarios se abren mediante la instalación de ASP.NET y el depurador remoto. Sin embargo, es posible que deba comprobar que los puertos están abiertos.

> [!NOTE]
> En una máquina virtual de Azure, debe abrir puertos a través del [grupo de seguridad](/azure/virtual-machines/windows/nsg-quickstart-portal)de red .

Puertos requeridos:

* 80 - Requerido para IIS
::: moniker range=">=vs-2019"
* 4024 - Necesario para la depuración remota desde Visual Studio 2019 (consulte [Asignaciones](../debugger/remote-debugger-port-assignments.md) de puertos del depurador remoto para obtener más información).
::: moniker-end
::: moniker range="vs-2017"
* 4022 - Necesario para la depuración remota desde Visual Studio 2017 (consulte [Asignaciones](../debugger/remote-debugger-port-assignments.md) de puertos del depurador remoto para obtener más información).
::: moniker-end
* UDP 3702 - (Opcional) puerto de detección le permite el botón **Buscar** al asociar al depurador remoto en Visual Studio.

1. Para abrir un puerto en Windows Server, abra el menú **Inicio** y busque Firewall de **Windows con seguridad avanzada**.

2. A continuación, elija **Reglas de entrada > Nueva regla > puerto**y, a continuación, haga clic en **Siguiente**. (Para UDP 3702, elija **las reglas de salida** en su lugar.)

3. En **Puertos locales específicos**, ingrese el número de puerto, haga clic **después**.

4. Haga clic **en Permitir la conexión**, haga clic en **Siguiente**.

5. Seleccione uno o más tipos de red para habilitar el puerto y haga clic en **Siguiente**.

    Los tipos seleccionados deben incluir la red a la que está conectado el equipo remoto.
6. Agregue el nombre (por ejemplo, **IIS**, **Web Deploy**o **msvsmon**) para la regla de entrada y haga clic en **Finalizar**.

    Debería ver la nueva regla en la lista Reglas de entrada o Reglas de salida.

    Si desea obtener más detalles sobre la configuración del Firewall de Windows, consulte Configurar el Firewall de [Windows para la depuración remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Cree reglas adicionales para los otros puertos necesarios.
