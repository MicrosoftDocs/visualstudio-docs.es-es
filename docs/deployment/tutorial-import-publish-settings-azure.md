---
title: Publicar en Azure mediante la importación de configuración de publicación
ms.custom: Create and import a publishing profile to deploy an application from Visual Studio to Azure App Service
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
ms.openlocfilehash: 3e844e2177d01d5b308472eae5661b25798f0838
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/11/2018
---
# <a name="publish-an-application-to-azure-app-service-by-importing-publish-settings-in-visual-studio"></a>Publicar una aplicación en el servicio de aplicaciones de Azure mediante la importación de configuración de publicación en Visual Studio

Puede usar el **publicar** herramienta para importar configuración de publicación y, a continuación, implementar la aplicación. En este artículo, se utiliza configuración de publicación de servicio de aplicaciones de Azure, pero puede utilizar pasos similares para importar publicación la configuración de [IIS](../deployment/tutorial-import-publish-settings-iis.md). En algunos escenarios, el uso de una perfil de configuración puede ser más rápida que la configuración manual de implementación para el servicio para cada instalación de Visual Studio de publicación.

Estos pasos se aplican a las aplicaciones ASP.NET, ASP.NET Core y .NET Core en Visual Studio. También puede importar configuración de publicación de [Python](/visualstudio/python/publishing-python-web-applications-to-azure-from-visual-studio) aplicaciones. Los pasos se corresponden con Visual Studio 2017 versión 15.6.

En este tutorial va a:

> [!div class="checklist"]
> * Generar un archivo de configuración de publicación de servicio de aplicaciones de Azure
> * Importar el archivo de configuración de publicación en Visual Studio
> * Implementar la aplicación en el servicio de aplicaciones de Azure

Un archivo de configuración de publicación (*\*.publishsettings*) es diferente de un perfil de publicación (*\*.pubxml*) creados en Visual Studio. Un archivo de configuración de publicación se crea el servicio de aplicación de Azure y, a continuación, se puede importar en Visual Studio.

> [!NOTE]
> Si desea copiar un perfil de publicación en Visual Studio (*\*.pubxml* archivo) desde una instalación de Visual Studio, puede encontrar el perfil de publicación,  *\<profilename\>.pubxml*, en la  *\\< NombreDeProyecto\>\Properties\PublishProfiles* carpeta para tipos de proyectos administrados. Para los sitios Web, busque en el *\App_Data* carpeta. Los perfiles de publicación son archivos XML de MSBuild.

## <a name="prerequisites"></a>Requisitos previos

* Debe tener instalado Visual Studio y la **ASP.NET** y **.NET Framework** cargas de trabajo de desarrollo. Para una aplicación .NET Core, también necesitará el **.NET Core** carga de trabajo.

    Si todavía no tiene instalado Visual Studio, puede descargarlo de forma gratuita en [esta página](http://www.visualstudio.com).

* Crear un servicio de aplicaciones de Azure. Para obtener instrucciones detalladas, consulte [implementar una aplicación web de ASP.NET Core en Azure con Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). 

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Crear un nuevo proyecto ASP.NET en Visual Studio

1. En el equipo que ejecuta Visual Studio, elija **archivo > Nuevo proyecto**.

1. En **Visual C#** o **Visual Basic**, elija **Web**y, a continuación, en el panel central elija **aplicación Web de ASP.NET (.NET Framework)**(solo C#) o **aplicación Web de ASP.NET Core**y, a continuación, haga clic en **Aceptar**.

    Si no ve las plantillas de proyecto especificado, haga clic en el **abrir Visual Studio Installer** vínculo en el panel izquierdo de la **nuevo proyecto** cuadro de diálogo. Se iniciará el Instalador de Visual Studio. Consulte los requisitos previos de este artículo para identificar las cargas de trabajo de Visual Studio necesarios, que se deben instalar.

1. Elija **MVC** (.NET Framework) o **aplicación Web (Model-View-Controller)** (para .NET Core) y asegúrese de que **sin autenticación** está seleccionada y, a continuación, haga clic en **Aceptar**.

1. Escriba un nombre como **MyWebApp** y haga clic en **Aceptar**.

    Visual Studio crea el proyecto.

1. Elija **generar > compilar solución** para compilar el proyecto.

## <a name="create-the-publish-settings-file-in-azure-app-service"></a>Crear el archivo de configuración de publicación en el servicio de aplicación de Azure

1. En el portal de Azure, abra el servicio de aplicaciones de Azure.

1. Haga clic en **Get perfil de publicación** y guarde el perfil local.

    ![Obtener el perfil de publicación](../deployment/media/tutorial-azure-app-service-get-publish-profile.png)

    Un archivo con un *.publishsettings* extensión de archivo se ha generado desde la ubicación donde guardó. El código siguiente muestra un ejemplo parcial del archivo (en un formato más legible).

    ```xml
    <publishData>
      <publishProfile
        profileName="DeployASPDotNetCore - Web Deploy"
        publishMethod="MSDeploy"
        publishUrl="deployaspdotnetcore.scm.azurewebsites.net:443"
        msdeploySite="DeployASPDotNetCore"
        userName="$DeployASPDotNetCore"
        userPWD="abcdefghijklmnopqrstuzwxyz"
        destinationAppUrl="http://deployaspdotnetcore20180508031824.azurewebsites.net"
        SQLServerDBConnectionString=""
        mySQLDBConnectionString=""
        hostingProviderForumLink=""
        controlPanelLink="http://windows.azure.com"
        webSystem="WebSites">
        <databases />
      </publishProfile>
    </publishData>
    ```
    Normalmente, el archivo *.publishsettings anterior contiene dos perfiles de publicación que pueden usar en Visual Studio, uno para la implementación con Web Deploy y otro para implementar mediante FTP. El código anterior muestra el perfil de Web Deploy. Ambos perfiles se importarán más adelante al importar el perfil.

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importar la configuración de publicación en Visual Studio e implementar

1. En el equipo donde tiene el proyecto ASP.NET abierto en Visual Studio, haga clic en el proyecto en el Explorador de soluciones y elija **publicar**.

1. Si previamente ha configurado ningún perfil de publicación, la **publicar** aparece el panel. Haga clic en **crear nuevo perfil**.

1. En el **elegir un destino de publicación** cuadro de diálogo, haga clic en **importar perfil**.

    ![Elija publicar](../deployment/media/tutorial-publish-tool-import-profile.png)

1. Navegue hasta la ubicación del archivo de configuración de publicación que ha creado en la sección anterior.

1. En el **importar el archivo de configuración de publicación** cuadro de diálogo, seleccione el perfil que creó en la sección anterior y haga clic en **abiertos**.

1. Seleccione uno de los dos perfiles importados y haga clic en **publicar**.

    Visual Studio inicia el proceso de implementación y la ventana de salida muestra el progreso y los resultados.

## <a name="next-steps"></a>Pasos siguientes

En este tutorial, creó un archivo de configuración de publicación, había importado en Visual Studio e implementa una aplicación ASP.NET en el servicio de aplicaciones de Azure.

> [!div class="nextstepaction"]
> [Primer vistazo a la implementación](../deployment/deploying-applications-services-and-components.md)
