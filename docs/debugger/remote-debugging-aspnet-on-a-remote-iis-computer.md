---
title: Depuración remota de ASP.NET Core en un equipo remoto de IIS | Microsoft Docs
ms.custom: remotedebugging
ms.date: 05/21/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: d9515d208f2ab4bb8c429d5063e5134676c71c24
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38785962"
---
# <a name="remote-debug-aspnet-core-on-a-remote-iis-computer-in-visual-studio-2017"></a>Depuración remota de ASP.NET Core en un equipo remoto de IIS en Visual Studio 2017
Para depurar una aplicación ASP.NET que se ha implementado en IIS, instalar y ejecutar las herramientas remotas en el equipo donde ha implementado la aplicación y, a continuación, adjunte a su aplicación en ejecución desde Visual Studio.

![Componentes del depurador remoto](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

Esta guía explica cómo configurar y configurar un núcleo de ASP.NET de Visual Studio 2017, implementarla en IIS y asociar al depurador remoto de Visual Studio. Para la depuración remota de ASP.NET 4.5.2, consulte [ASP.NET de depuración remota en un equipo de IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). También puede implementar y depurar en IIS con Azure. Para Azure App Service, fácilmente puede implementar y depurar en una instancia de IIS y el depurador remoto mediante preconfigurada el [Snapshot Debugger](../debugger/debug-live-azure-applications.md) o [asociar el depurador del explorador de servidores](../debugger/remote-debugging-azure.md).

Estos procedimientos se han probado en estas configuraciones de servidor:
* Windows Server 2012 R2 y IIS 8
* Windows Server 2016 e IIS 10

## <a name="requirements"></a>Requisitos

No se admite la depuración entre dos equipos conectados a través de un servidor proxy. Depuración mediante una conexión de ancho de banda bajo, por ejemplo, acceso telefónico a Internet, o una latencia alta o a través de Internet entre países no se recomienda y puede ser un error o inaceptablemente bajo. Para obtener una lista completa de requisitos, consulte [requisitos](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="app-already-running-in-iis"></a>¿Aplicación ya que se ejecuta en IIS?

En este artículo incluye pasos sobre cómo configurar una configuración básica de IIS en Windows server y la implementación de la aplicación desde Visual Studio. Estos pasos se incluyen para asegurarse de que el servidor ha requerido componentes instalados, que puede ejecutar correctamente la aplicación y que está listo para la depuración remota.

* Si la aplicación se ejecuta en IIS y simplemente desea descargar el depurador remoto e iniciar la depuración, vaya a [descargar e instalar las herramientas remotas en Windows Server](#BKMK_msvsmon).

* Si desea obtener ayuda para asegurarse de que la aplicación se ha configurado, implementado y que se ejecutan correctamente en IIS para que pueda Depurar, siga todos los pasos de este tema.

## <a name="create-the-aspnet-core-application-on-the-visual-studio-2017-computer"></a>Crear la aplicación de ASP.NET Core en el equipo de Visual Studio 2017 

1. Cree una nueva aplicación de ASP.NET Core. (**Archivo > Nuevo > proyecto**, a continuación, seleccione **Visual C# > Web > aplicación Web ASP.NET Core**).

    En el **ASP.NET Core** sección plantillas, seleccione **aplicación Web**.

2. Asegúrese de que **ASP.NET Core 2.0** está seleccionada, que **habilitar la compatibilidad con Docker** es **no** seleccionada y que **autenticación** está establecido en **Sin autenticación**.

3. Denomine el proyecto **MyASPApp** y haga clic en **Aceptar** para crear la nueva solución.

4. Abra el archivo About.cshtml.cs y establecer un punto de interrupción en el `OnGet` método (en las plantillas anteriores, abra HomeController.cs en su lugar y establezca el punto de interrupción en el `About()` método).

## <a name="bkmk_configureIIS"></a> Instalar y configurar IIS en Windows Server

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Actualizar configuración de seguridad del explorador en Windows Server

Si está habilitada la configuración de seguridad mejorada de Internet Explorer (está habilitado de forma predeterminada), es posible que deba agregar algunos dominios como sitios de confianza para que pueda descargar algunos de los componentes de servidor web. Agregar los sitios de confianza, vaya a **opciones de Internet > seguridad > sitios de confianza > sitios**. Agregue los siguientes dominios.

- Microsoft.com
- go.microsoft.com
- download.microsoft.com
- IIS.NET

Al descargar el software, obtendrá las solicitudes para conceder permiso para cargar varios scripts de sitios web y recursos. Algunos de estos recursos no son necesarias, pero para simplificar el proceso, haga clic en **agregar** cuando se le solicite.

## <a name="install-aspnet-core-on-windows-server"></a>Instalación de ASP.NET Core en Windows Server

1. Instalar el [hospedaje de .NET Core Windows Server](https://aka.ms/dotnetcore-2-windowshosting) agrupación en el sistema host. El módulo ASP.NET Core, biblioteca de .NET Core y .NET Core Runtime, instala la agrupación. Para obtener más instrucciones, consulte [publicar en IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    > [!NOTE]
    > Si el sistema no tiene una conexión a Internet, obtenga e instale el *[Microsoft Visual C++ 2015 Redistributable](https://www.microsoft.com/download/details.aspx?id=53840)* antes de instalar la agrupación de hospedaje de .NET Core Windows Server.

3. Reinicie el sistema (o ejecute **net stop was /y** seguido **del comando net start w3svc** desde un símbolo del sistema para recoger un cambio en la ruta de acceso del sistema).

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

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importar la configuración de publicación en Visual Studio e implementar

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Después de la aplicación se implementa correctamente, debe iniciarse automáticamente. Si la aplicación no se inicia desde Visual Studio, inicie la aplicación en IIS. Para ASP.NET Core, deberá asegurarse de que el grupo de aplicaciones de campo para el **DefaultAppPool** está establecido en **sin código administrado**.

1. En el **configuración** cuadro de diálogo, habilitar la depuración haciendo **siguiente**, elija un **depurar** configuración y, a continuación, elija **quitar archivos adicionales en destino** bajo el **Publicar archivo** opciones.

    > [!NOTE]
    > Si elige una configuración de lanzamiento, deshabilite la depuración en el *web.config* archivo al publicar.

1. Haga clic en **guardar** y, a continuación, volver a publicar la aplicación.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(Opcional) Implementar mediante la publicación en una carpeta local

Puede usar esta opción para implementar la aplicación si van a copiar la aplicación en IIS mediante Powershell, RoboCopy, o desea copiar manualmente los archivos.

### <a name="BKMK_deploy_asp_net"></a> Configurar el sitio Web de ASP.NET en el equipo de Windows Server

1. Abra el Explorador de Windows y cree una nueva carpeta, **C:\Publish**, donde posteriormente implementará el proyecto ASP.NET.

2. Si aún no está abierto, abra el **Internet Information Services (IIS) Manager**. (En el panel izquierdo del administrador del servidor, seleccione **IIS**. Haga clic en el servidor y seleccione **Internet Information Services (IIS) Manager**.)

3. En **conexiones** en el panel izquierdo, vaya a **sitios**.

4. Seleccione el **sitio Web predeterminado**, elija **configuración básica**y establezca el **ruta de acceso física** a **C:\Publish**.

4. Haga clic con el botón secundario en el nodo **Sitio web predeterminado** y seleccione **Agregar aplicación**.

5. Establecer el **Alias** campo **MyASPApp**, acepte el valor predeterminado de grupo de aplicaciones (**DefaultAppPool**) y establezca el **ruta de acceso física** a  **C:\Publish**.

6. En **conexiones**, seleccione **grupos de aplicaciones**. Abra **DefaultAppPool** y establezca el campo de grupo de aplicaciones en **sin código administrado**.

7. Haga clic en el nuevo sitio en el Administrador de IIS, elija **Editar permisos**y asegúrese de que ese IUSR, IIS_IUSRS o el usuario configurado para el acceso a la aplicación web es un usuario autorizado con derechos de lectura y ejecución.

    Si no ve uno de estos usuarios con acceso, siga los pasos para agregar IUSR como un usuario con derechos de lectura y ejecución.

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Publicar e implementar la aplicación mediante la publicación en una carpeta local desde Visual Studio

También puede publicar y distribuir la aplicación mediante el sistema de archivos u otras herramientas.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="BKMK_msvsmon"></a> Descargue e instale las herramientas remotas en Windows Server

En este tutorial, estamos usando Visual Studio 2017.

Si tiene problemas para abrir la página con la descarga del depurador remoto, consulte [desbloquear la descarga del archivo](../debugger/remote-debugging.md#unblock_msvsmon) para obtener ayuda.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> En algunos escenarios, puede ser más eficaz para ejecutar al depurador remoto desde un recurso compartido de archivos. Para obtener más información, consulte [ejecutar el depurador remoto desde un recurso compartido de archivos](../debugger/remote-debugging.md#fileshare_msvsmon).
  
## <a name="BKMK_setup"></a> Configurar el depurador remoto en Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Si necesita agregar permisos para usuarios adicionales, cambiar el modo de autenticación, o número de puerto para el depurador remoto, consulte [configurar el depurador remoto](../debugger/remote-debugging.md#configure_msvsmon).

Para obtener información acerca de cómo ejecutar el depurador remoto como un servicio, consulte [ejecutar el depurador remoto como un servicio](../debugger/remote-debugging.md#bkmk_configureService).

## <a name="BKMK_attach"></a> Adjuntar elementos a la aplicación ASP.NET desde el equipo de Visual Studio

1. En el equipo de Visual Studio, abra la solución que está intentando depurar (**MyASPApp** si está siguiendo todos los pasos de este artículo).
2. En Visual Studio, haga clic en **Depurar > asociar al proceso** (Ctrl + Alt + P).

    > [!TIP]
    > En Visual Studio 2017, puede volver a adjuntar al mismo proceso adjuntado previamente, utilizando **Depurar > adjuntar al proceso...** (Mayús + Alt + P). 

3. Establezca el campo calificador en  **\<nombre del equipo remoto >: 4022**.
4. Haga clic en **Actualizar**.
    Debería ver que algunos procesos aparecen en la ventana **Procesos disponibles** .

    Si no ve todos los procesos, pruebe a usar la dirección IP en lugar del nombre del equipo remoto (el puerto es necesario). Puede usar `ipconfig` en una línea de comandos para obtener la dirección IPv4.

    Si desea usar el **buscar** botón, es posible que deba [abrir el puerto UDP 3702](#bkmk_openports) en el servidor.

5. Active  **Mostrar los procesos de todos los usuarios**.
6. Escriba la primera letra de un nombre de proceso para encontrar rápidamente **dotnet.exe** (para ASP.NET Core).

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg_attachtoprocess_aspnetcore.png "RemoteDBG_AttachToProcess")

7. Haga clic en **Adjuntar**.

8. Abra el sitio web del equipo remoto. En un explorador, vaya a **http://\<nombre del equipo remoto >**.
    
    Debería ver la página web de ASP.NET.

9. En la aplicación ASP.NET en ejecución, haga clic en el vínculo a la **sobre** página.

    Se alcanzará el punto de interrupción en Visual Studio.

## <a name="bkmk_openports"></a> Solución de problemas: Abra los puertos necesarios en Windows Server

En la mayoría de las instalaciones, se abren los puertos requeridos por la instalación de ASP.NET y el depurador remoto. Sin embargo, deberá comprobar que los puertos estén abiertos.

> [!NOTE]
> En una máquina virtual de Azure, debe abrir los puertos a través de la [grupo de seguridad de red](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80-for-web-traffic).

Puertos necesarios:

- 80 - necesarias para IIS
- 4022 - necesarios para la depuración remota desde Visual Studio 2017 (consulte [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md) para obtener información detallada.
- 8172: (opcional) necesario para que Web Deploy implementar la aplicación desde Visual Studio.
- UDP 3702 - puerto de detección (opcional) permite la **buscar** botón al asociar el depurador remoto en Visual Studio.

1. Para abrir un puerto en Windows Server, abra el **iniciar** menú, busque **Firewall de Windows con seguridad avanzada**.

2. A continuación, elija **reglas de entrada > nueva regla > puerto**y, a continuación, haga clic en **siguiente**. (Para UDP 3702, elija **reglas de salida** en su lugar.)

3. En **puertos locales específicos**, escriba el número de puerto, haga clic en **siguiente**.

4. Haga clic en **permitir la conexión**, haga clic en **siguiente**.

5. Seleccione uno o varios tipos de red para habilitar para el puerto y haga clic en **siguiente**.

    Los tipos seleccionados deben incluir la red a la que está conectado el equipo remoto.
6. Agregue el nombre (por ejemplo, **IIS**, **Web Deploy**, o **msvsmon**) para la regla de entrada y haga clic en **finalizar**.

    Debería ver la nueva regla en la lista de reglas de entrada o las reglas de salida.

    Si desea obtener más información sobre cómo configurar Firewall de Windows, consulte [configurar el Firewall de Windows para la depuración remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Cree reglas adicionales para los otros puertos necesarios.
