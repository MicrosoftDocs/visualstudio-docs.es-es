---
title: Remoto depurar en un equipo remoto de IIS, ASP.NET | Documentos de Microsoft
ms.custom: remotedebugging
ms.date: 05/21/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 9cb339b5-3caf-4755-aad1-4a5da54b2a23
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 759615311478f1b428edc2a800c61b9252a3a84a
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34746863"
---
# <a name="remote-debug-aspnet-on-a-remote-iis-computer"></a>Depuración remota en un equipo remoto de IIS, ASP.NET
Para depurar una aplicación ASP.NET que se ha implementado en IIS, instalar y ejecutar las herramientas remotas en el equipo donde se implementa la aplicación y, a continuación, adjunte a su aplicación en ejecución desde Visual Studio.

![Los componentes del depurador remoto](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

Esta guía explica cómo instalar y configurar una aplicación de Visual Studio de 2017 ASP.NET MVC 4.5.2, implementarla en IIS y adjuntar al depurador remoto de Visual Studio.

> [!NOTE]
> Remoto depurar ASP.NET Core en su lugar, consulte [remoto depurar ASP.NET Core en un equipo con IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md). Para el servicio de aplicación de Azure, facilidad puede implementar y depurar en una instancia preconfigurada de IIS mediante el [depurador instantánea](../debugger/debug-live-azure-applications.md) (.NET 4.6.1 necesario) o por [para asociar el depurador del explorador de servidores](../debugger/remote-debugging-azure.md).

Estos procedimientos se han probado en estas configuraciones de servidor:
* Windows Server 2012 R2 y IIS 8 (para Windows Server 2008 R2, los pasos del servidor son diferentes)

## <a name="requirements"></a>Requisitos

El depurador remoto es compatible con Windows Server a partir de Windows Server 2008 Service Pack 2. Para obtener una lista completa de requisitos, consulte [requisitos](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> No se admite la depuración entre dos equipos conectados a través de un servidor proxy. Depuración mediante una conexión de poco ancho de banda, como acceso telefónico a Internet, o una latencia alta o a través de Internet a través de países no se recomienda y puede ser un error o inaceptablemente bajo.

## <a name="app-already-running-in-iis"></a>¿Aplicación que se está ejecutando en IIS?

Este artículo incluye pasos sobre cómo configurar una configuración básica de IIS en Windows server y la implementación de la aplicación desde Visual Studio. Estos pasos se incluyen para asegurarse de que el servidor ha requerido componentes instalados, que la aplicación puede ejecutar correctamente y que está listo para realizar la depuración remota.

* Si la aplicación se ejecuta en IIS y desea descargar el depurador remoto y para iniciar la depuración, vaya a [descargar e instalar las herramientas remotas en Windows Server](#BKMK_msvsmon).

* Si desea obtener ayuda para asegurarse de la aplicación está configurada, implementa y ejecute correctamente en IIS para que puedan depurar, siga todos los pasos de este tema.

## <a name="create-the-aspnet-452-application-on-the-visual-studio-computer"></a>Crear ASP.NET 4.5.2 aplicación en el equipo de Visual Studio
  
1. Cree una nueva aplicación de MVC ASP.NET (**Archivo > Nuevo > proyecto**, a continuación, seleccione ** Visual C# > Web > aplicación Web ASP.NET. En la sección de plantillas **ASP.NET 4.5.2** , seleccione **MVC**. Asegúrese de que **habilitar la compatibilidad con Docker** no está seleccionada y que **autenticación** está establecido en **sin autenticación**. Denomine el proyecto **MyASPApp**.)

2. Abra el archivo HomeController.cs y establezca un punto de interrupción en el método `About()` .

## <a name="bkmk_configureIIS"></a> Instalar y configurar IIS en Windows Server

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Actualizar la configuración de seguridad del explorador en Windows Server

Si está habilitada la configuración de seguridad mejorada de Internet Explorer (está habilitado de forma predeterminada), debe agregar algunos dominios como sitios de confianza para que le permitirán descargar algunos de los componentes de servidor web. Agregar los sitios de confianza, vaya a **opciones de Internet > seguridad > sitios de confianza > sitios**. Agregue los dominios siguientes.

- Microsoft.com
- go.microsoft.com
- download.microsoft.com
- IIS.NET

Al descargar el software, puede obtener las solicitudes para conceder permiso para cargar varias secuencias de comandos del sitio web y recursos. Algunos de estos recursos no son necesarias, pero para simplificar el proceso, haga clic en **agregar** cuando se le solicite.

## <a name="BKMK_deploy_asp_net"></a> Instalar ASP.NET 4.5 en Windows Server

Si desea información más detallada para instalar ASP.NET en IIS, consulte [IIS 8.0 utilizando ASP.NET 3.5 y 4.5 de ASP.NET](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

1. En el panel izquierdo del administrador del servidor, seleccione **IIS**. Haga clic en el servidor y seleccione **Internet Information Services (IIS) Manager**.

1. Utilice el instalador de plataforma Web (WPI) para instalar ASP.NET 4.5 (en el nodo del servidor en Windows Server 2012 R2, elija **obtener nuevos componentes de plataforma de Web** y, a continuación, busque ASP.NET)

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg_iis_aspnet_45.png "RemoteDBG_IIS_AspNet_45")

    > [!NOTE]
    > Si está utilizando Windows Server 2008 R2, instale ASP.NET 4 en lugar de utilizar este comando:

     **C:\Windows\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -ir**

2. Reiniciar el sistema (o ejecutar **net stop era /y** seguido **del comando net start w3svc** desde un símbolo del sistema para recoger un cambio en la ruta de acceso del sistema).

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

Después de que la aplicación se implementa correctamente, debe iniciarse automáticamente. Si la aplicación no se inicia desde Visual Studio, inicie la aplicación en IIS.

1. En el **configuración** cuadro de diálogo, Habilitar depuración haciendo clic en **siguiente**, elija un **depurar** configuración y, a continuación, elija **quitar archivos adicionales en destino** en el **Publicar archivo** opciones.

    > [!NOTE]
    > Si elige una configuración de lanzamiento, deshabilite la depuración en el *web.config* archivos al publicar.

1. Haga clic en **guardar** y, a continuación, volver a publicar la aplicación.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(Opcional) Implementar mediante la publicación en una carpeta local

Puede usar esta opción para implementar la aplicación si van a copiar la aplicación en IIS con Powershell, RoboCopy, o desea copiar manualmente los archivos.

### <a name="BKMK_deploy_asp_net"></a> Configurar el sitio Web de ASP.NET en el equipo de Windows Server

1. Abra el Explorador de Windows y cree una nueva carpeta, **C:\Publish**, donde va a implementar el proyecto ASP.NET más adelante.

2. Si no está ya abierto, abra el **Internet Information Services (IIS) Manager**. (En el panel izquierdo del administrador del servidor, seleccione **IIS**. Haga clic en el servidor y seleccione **Internet Information Services (IIS) Manager**.)

3. En **conexiones** en el panel izquierdo, vaya a **sitios**.

4. Seleccione el **sitio Web predeterminado**, elija **configuración básica**y establezca el **ruta de acceso física** a **C:\Publish**.

5. Haga clic con el botón secundario en el nodo **Sitio web predeterminado** y seleccione **Agregar aplicación**.

6. Establecer el **Alias** campo **MyASPApp**, acepte el valor predeterminado de grupo de aplicaciones (**DefaultAppPool**) y establezca el **ruta de acceso física** a  **C:\Publish**.

7. En **conexiones**, seleccione **grupos de aplicaciones**. Abra **DefaultAppPool** y establezca el campo de grupo de aplicaciones en **ASP.NET v4.0** (ASP.NET 4.5 no es una opción para el grupo de aplicaciones).

8. Con el sitio seleccionado en el Administrador de IIS, elija **Editar permisos**y asegúrese de que ese IUSR, IIS_IUSRS o el usuario configurado para el grupo de aplicaciones es un usuario autorizado con permisos de lectura y ejecución. Si ninguno de estos usuarios están presente, agregue IUSR como un usuario con derechos de lectura y ejecución.

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Publique e implemente la aplicación al realizar la publicación en una carpeta local de Visual Studio

También puede publicar e implementar la aplicación mediante el sistema de archivos u otras herramientas.

1. (ASP.NET 4.5.2) Asegúrese de que el archivo web.config muestra la versión correcta de .NET Framework.  Por ejemplo, si desea usar ASP.NET 4.5.2, asegúrese de que esta versión se muestra en el archivo web.config.
  
    ```xml
    <system.web>
      <compilation debug="true" targetFramework="4.5.2" />
      <httpRuntime targetFramework="4.5.2" />
      <httpModules>
        <add name="ApplicationInsightsWebTracking" type="Microsoft.ApplicationInsights.Web.ApplicationInsightsHttpModule, Microsoft.AI.Web" />
      </httpModules>
    </system.web>
  
    ```

    Por ejemplo, la versión debe ser 4.0 si instala ASP.NET 4 en lugar de 4.5.2.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="BKMK_msvsmon"></a> Descargue e instale las herramientas remotas en Windows Server

En este tutorial, estamos utilizando Visual Studio de 2017.

Si tiene problemas para abrir la página con la descarga del depurador remoto, consulte [desbloquear la descarga del archivo](../debugger/remote-debugging.md#unblock_msvsmon) para obtener ayuda.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> En algunos casos, puede ser más eficaz para ejecutar al depurador remoto desde un recurso compartido de archivos. Para obtener más información, consulte [ejecutar el depurador remoto desde un recurso compartido de archivos](../debugger/remote-debugging.md#fileshare_msvsmon).
  
## <a name="BKMK_setup"></a> Configurar el depurador remoto en Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Si necesita agregar permisos para los usuarios adicionales, cambiar el modo de autenticación o número de puerto para el depurador remoto, consulte [configurar el depurador remoto](../debugger/remote-debugging.md#configure_msvsmon).

Para obtener información acerca de cómo ejecutar el depurador remoto como un servicio, consulte [ejecutar el depurador remoto como un servicio](../debugger/remote-debugging.md#bkmk_configureService).

## <a name="BKMK_attach"></a> Adjuntar elementos a la aplicación ASP.NET desde el equipo de Visual Studio

1. En el equipo de Visual Studio, abra la solución que está intentando depurar (**MyASPApp** si está siguiendo los pasos descritos en este artículo).
2. En Visual Studio, haga clic en **Depurar > asociar al proceso** (Ctrl + Alt + P).

    > [!TIP]
    > En Visual Studio de 2017, puede volver a adjuntar al mismo proceso que ha asociado previamente a mediante el uso de **Depurar > volver a adjuntar al proceso...** (Mayús + Alt + P). 

3. Establezca el campo calificador en  **\<nombre del equipo remoto >: 4022**.
4. Haga clic en **Actualizar**.
    Debería ver que algunos procesos aparecen en la ventana **Procesos disponibles** .

    Si no ve todos los procesos, pruebe a usar la dirección IP en lugar del nombre del equipo remoto (el puerto es necesario). Puede usar `ipconfig` en una línea de comandos para obtener la dirección IPv4.

5. Active  **Mostrar los procesos de todos los usuarios**.
6. Escriba la primera letra de un nombre de proceso para encontrar rápidamente **w3wp.exe** para ASP.NET 4.5.

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg_attachtoprocess.png "RemoteDBG_AttachToProcess")

7. Haga clic en **adjuntar**

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
- 8172 - (opcional) necesarios para que Web Deploy implementar la aplicación desde Visual Studio
- 4022 - necesarios para la depuración remota de Visual Studio de 2017 (vea [asignaciones de puerto de depurador remoto](../debugger/remote-debugger-port-assignments.md) para obtener información detallada.
- UDP 3702 - puerto de detección (opcional) permite la **buscar** botón al adjuntar el depurador remoto en Visual Studio.

1. Para abrir un puerto de servidor de Windows, abra la **iniciar** menú, busque **Firewall de Windows con seguridad avanzada**.

2. A continuación, elija **reglas de entrada > nueva regla > puerto**. Elija **siguiente** y en **puertos locales específicos**, escriba el número de puerto, haga clic en **siguiente**, a continuación, **permitir la conexión**, haga clic en siguiente, y Agregue el nombre (**IIS**, **Web Deploy**, o **msvsmon**) para la regla de entrada.

    Si desea obtener más información acerca de cómo configurar Firewall de Windows, vea [configurar Firewall de Windows para la depuración remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Cree reglas adicionales para los otros puertos necesarios.