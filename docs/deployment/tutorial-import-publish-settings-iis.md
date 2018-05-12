---
title: Publicar en IIS mediante la importación de la configuración de publicación
ms.custom: Create and import a publishing profile to deploy an application from Visual Studio to IIS
ms.date: 05/07/2018
ms.technology: vs-ide-deployment
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b023349454f71835e13e7cc891b8be92b90c153f
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/11/2018
---
# <a name="publish-an-application-to-iis-by-importing-publish-settings-in-visual-studio"></a>Publicar una aplicación en IIS mediante la importación de configuración de publicación en Visual Studio

Puede usar el **publicar** herramienta para importar configuración de publicación y, a continuación, implementar la aplicación. En este artículo, se utiliza configuración de publicación de IIS, pero puede utilizar pasos similares para importar configuración de publicación de [servicio de aplicaciones de Azure](../deployment/tutorial-import-publish-settings-azure.md). En algunos escenarios, el uso de una perfil de configuración puede ser más rápida que la configuración manual de implementación en IIS para cada instalación de Visual Studio de publicación.

Estos pasos se aplican a las aplicaciones ASP.NET, ASP.NET Core y .NET Core en Visual Studio. Los pasos se corresponden con Visual Studio 2017 versión 15.6.

En este tutorial va a:

> [!div class="checklist"]
> * Configurar IIS para que pueda generar un archivo de configuración de publicación
> * Crear un archivo de configuración de publicación
> * Importar el archivo de configuración de publicación en Visual Studio
> * Implementar la aplicación en IIS

Un archivo de configuración de publicación (*\*.publishsettings*) es diferente de un perfil de publicación (*\*.pubxml*) creados en Visual Studio. Se crea un archivo de configuración de publicación mediante IIS o servicio de aplicaciones de Azure, o se puede crear manualmente y, a continuación, se puede importar en Visual Studio.

> [!NOTE]
> Si desea copiar un perfil de publicación en Visual Studio (\*archivo .pubxml) desde una instalación de Visual Studio, puede encontrar el perfil de publicación,  *\<profilename\>.pubxml*, en el  *\\< NombreDeProyecto\>\Properties\PublishProfiles* carpeta para tipos de proyectos administrados. Para los sitios Web, busque en el *\App_Data* carpeta. Los perfiles de publicación son archivos XML de MSBuild.

## <a name="prerequisites"></a>Requisitos previos

* Debe tener instalado Visual Studio y la **ASP.NET** y **.NET Framework** cargas de trabajo de desarrollo. Para una aplicación .NET Core, también necesitará el **.NET Core** carga de trabajo.

    Si todavía no tiene instalado Visual Studio, puede descargarlo de forma gratuita en [esta página](http://www.visualstudio.com).

    Los pasos descritos en este artículo se basan en Visual Studio de 2017

* Para generar el archivo de configuración de publicación de IIS, debe tener un equipo que ejecuta Windows Server 2012 con el rol de servidor Web de IIS 8.0 correctamente configurado y 4.5 de ASP.NET o ASP.NET Core instalado. Para ASP.NET Core, vea [publicar en IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration). Para ASP.NET 4.5, consulte [IIS 8.0 utilizando ASP.NET 3.5 y 4.5 de ASP.NET](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Crear un nuevo proyecto ASP.NET en Visual Studio

1. En el equipo que ejecuta Visual Studio, elija **archivo > Nuevo proyecto**.

1. En **Visual C#** o **Visual Basic**, elija **Web**y, a continuación, en el panel central elija **aplicación Web de ASP.NET (.NET Framework)**(solo C#) o **aplicación Web de ASP.NET Core**y, a continuación, haga clic en **Aceptar**.

    Si no ve las plantillas de proyecto especificado, haga clic en el **abrir Visual Studio Installer** vínculo en el panel izquierdo de la **nuevo proyecto** cuadro de diálogo. Se iniciará el Instalador de Visual Studio. Consulte los requisitos previos de este artículo para identificar las cargas de trabajo de Visual Studio necesarios, que se deben instalar.

1. Elija **MVC** (.NET Framework) o **aplicación Web (Model-View-Controller)** (para .NET Core) y asegúrese de que **sin autenticación** está seleccionada y, a continuación, haga clic en **Aceptar**.

1. Escriba un nombre como **MyWebApp** y haga clic en **Aceptar**.

    Visual Studio crea el proyecto.

1. Elija **generar > compilar solución** para compilar el proyecto.

## <a name="install-and-configure-web-deploy-on-windows-server"></a>Instalar y configurar Web Deploy en Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

## <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Crear el archivo de configuración de publicación en IIS en Windows Server

1. En IIS, haga clic en el **sitio Web predeterminado**, elija **implementar** > **configurar implementar publicación en Web**.

    ![Establecer la configuración de Web Deploy](../deployment/media/tutorial-configure-web-deploy-publishing.png)

1. En el **configurar implementar publicación en Web** diálogo cuadro, examine la configuración.

1. Haga clic en **el programa de instalación**.

    En el **resultados** el panel, el resultado muestra que los derechos de acceso se concedió al usuario especificado y que un archivo con un *.publishsettings* extensión de archivo se ha generado desde la ubicación que aparece en el cuadro de diálogo.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <publishData>
      <publishProfile
        publishUrl="https://myhostname:8172/msdeploy.axd"
        msdeploySite="Default Web Site"
        destinationAppUrl="http://myhostname:80/"
        mySQLDBConnectionString=""
        SQLServerDBConnectionString=""
        profileName="Default Settings"
        publishMethod="MSDeploy"
        userName="myhostname\myusername" />
    </publishData>
    ```

    Según la configuración de IIS y Windows Server, verá valores diferentes. Estos son algunos detalles acerca de los valores que se ven:

    * El *msdeploy.axd* archivo mencionado en el `publishUrl` atributo es un archivo de controlador HTTP genera dinámicamente para Web Deploy. (Para realizar pruebas, `http://myhostname:8172` generalmente funcionará también.)
    * El `publishUrl` puerto normalmente se establece en el puerto 8172, que es el valor predeterminado de Web Deploy.
    * El `destinationAppUrl` puerto normalmente se establece en el puerto 80, que es el valor predeterminado de IIS.
    * Si no puede conectarse al host remoto en Visual Studio usando el nombre de host (en pasos posteriores), pruebe la dirección IP en lugar del nombre de host.

    > [!NOTE]
    > Si va a publicar en IIS que se ejecuta en una máquina virtual de Azure, se deben abrir los puertos IIS y Web Deploy en el grupo de seguridad de red. Para obtener información detallada, vea [instale y ejecute IIS](/azure/virtual-machines/windows/quick-create-portal#open-port-80-for-web-traffic).

1. Copie este archivo en el equipo donde se ejecuta Visual Studio.

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importar la configuración de publicación en Visual Studio e implementar

1. En el equipo donde tiene el proyecto ASP.NET abierto en Visual Studio, haga clic en el proyecto en el Explorador de soluciones y elija **publicar**.

1. Si previamente ha configurado ningún perfil de publicación, la **publicar** aparece el panel. Haga clic en **crear nuevo perfil**.

1. En el **elegir un destino de publicación** cuadro de diálogo, haga clic en **importar perfil**.

    ![Elija publicar](../deployment/media/tutorial-publish-tool-import-profile.png)

1. Navegue hasta la ubicación del archivo de configuración de publicación que ha creado en la sección anterior.

1. En el **importar el archivo de configuración de publicación** cuadro de diálogo, vaya a y seleccione el perfil que creó en la sección anterior y haga clic en **abiertos**.

    Visual Studio inicia el proceso de implementación y la ventana de salida muestra el progreso y los resultados.

    Si recibe una implementación de los errores, haga clic en **configuración** para editar la configuración. Modificar la configuración y haga clic en **validar** para probar la nueva configuración.

    ![Editar la configuración de la herramienta de publicación](../deployment/media/tutorial-configure-publish-settings-in-tool.png)

## <a name="next-steps"></a>Pasos siguientes

En este tutorial, creó un archivo de configuración de publicación, había importado en Visual Studio e implementa una aplicación ASP.NET en IIS.

> [!div class="nextstepaction"]
> [Primer vistazo a la implementación](../deployment/deploying-applications-services-and-components.md)
