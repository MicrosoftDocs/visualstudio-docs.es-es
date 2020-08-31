---
title: Publicar en Azure mediante la importación de la configuración de publicación
description: Creación e importación de un perfil de publicación para implementar una aplicación desde Visual Studio en Azure App Service
ms.date: 05/06/2020
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6d2c52d6db6ca3001712a692a1de059834c975ae
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/25/2020
ms.locfileid: "88801716"
---
# <a name="publish-an-application-to-azure-app-service-by-importing-publish-settings-in-visual-studio"></a>Publicar una aplicación en Azure App Service mediante la importación de la configuración de publicación a Visual Studio

Puede usar la herramienta **Publicar** para importar la configuración de publicación y después implementar la aplicación. En este artículo, se usa la configuración de publicación de Azure App Service, pero se pueden usar pasos similares para importar la configuración de publicación de [IIS](../deployment/tutorial-import-publish-settings-iis.md). En algunos escenarios, el uso de un perfil de configuración de publicación puede ser más rápido que configurar manualmente la implementación en el servicio para cada instalación de Visual Studio.

Estos pasos se aplican a aplicaciones ASP.NET, ASP.NET Core y .NET Core en Visual Studio. También puede importar la configuración de publicación de aplicaciones [Python](../python/publishing-python-web-applications-to-azure-from-visual-studio.md).

En este tutorial va a:

> [!div class="checklist"]
> * Generar un archivo de configuración de publicación de Azure App Service
> * Importar el archivo de configuración de publicación a Visual Studio
> * Implementar la aplicación en Azure App Service

Un archivo de configuración de publicación ( *\*.publishsettings*) es diferente a un perfil de publicación ( *\*.pubxml*) creado en Visual Studio. Un archivo de configuración de publicación se crea mediante Azure App Service y después puede importarse a Visual Studio.

> [!NOTE]
> Si tan solo necesita copiar un perfil de publicación de Visual Studio (archivo *\*.pubxml*) de una instalación de Visual Studio en otra, puede encontrar el perfil de publicación, *\<profilename\>.pubxml*, en la carpeta *\\<nombredeproyecto\>\Properties\PublishProfiles* correspondiente a los tipos de proyecto administrados. Para sitios web, busque en la carpeta *\App_Data*. Los perfiles de publicación son archivos XML de MSBuild.

## <a name="prerequisites"></a>Requisitos previos

::: moniker range=">=vs-2019"

* Debe tener instalado Visual Studio 2019 y la carga de trabajo **Desarrollo web y ASP.NET**.

    Si todavía no ha instalado Visual Studio, vaya a la página de  [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/)  para instalarlo de forma gratuita.
::: moniker-end

::: moniker range="vs-2017"

* Debe tener instalado Visual Studio 2017 y la carga de trabajo **Desarrollo web y ASP.NET**.

    Si todavía no ha instalado Visual Studio, vaya a la página de  [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/)  para instalarlo de forma gratuita.
::: moniker-end

* Cree una instancia de Azure App Service. Para obtener instrucciones detalladas, vea [Publicar una aplicación de ASP.NET Core en Azure con Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Crear un nuevo proyecto de ASP.NET en Visual Studio

1. En el equipo con Visual Studio, cree un proyecto.

    Elija la plantilla correcta. En este ejemplo, elija **Aplicación web ASP.NET (.NET Framework)** o (solo para C#) **Aplicación web ASP.NET Core** y seleccione **Aceptar**.

    Si no ve las plantillas de proyecto especificadas, vaya al vínculo **Abrir el instalador de Visual Studio** en el panel izquierdo del cuadro de diálogo **Nuevo proyecto**. Se iniciará el Instalador de Visual Studio. Instale la carga de trabajo **ASP.NET y desarrollo web**.

    La plantilla de proyecto que elija (ASP.NET o ASP.NET Core) debe coincidir con la versión de ASP.NET instalada en el servidor web.

1. Elija **MVC** (.NET Framework) o **Aplicación web (Modelo-Vista-Controlador)** (para .NET Core), compruebe que la opción **Sin autenticación** está seleccionada y luego seleccione **Aceptar**.

1. Escriba un nombre como **MyWebApp** y seleccione **Aceptar**.

    Visual Studio crea el proyecto.

1. Elija **Compilar** > **Compilar solución** para compilar el proyecto.

## <a name="create-the-publish-settings-file-in-azure-app-service"></a>Crear el archivo de configuración de publicación en Azure App Service

1. En Azure Portal, abra Azure App Service.

1. Vaya a **Obtener perfil de publicación** y guarde el perfil en local.

    ![Obtención del perfil de publicación](../deployment/media/tutorial-azure-app-service-get-publish-profile.png)

    Un archivo con una extensión de archivo *.publishsettings* se ha generado en la ubicación donde lo ha guardado. El código siguiente muestra un ejemplo parcial del archivo (en un formato más legible).

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

    Normalmente, el archivo *.publishsettings anterior contiene dos perfiles de publicación que puede usar en Visual Studio, uno para implementar mediante Web Deploy y otro para implementar mediante FTP. El código anterior muestra el perfil de Web Deploy. Ambos perfiles se importan más adelante al importar el perfil.

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importar la configuración de publicación a Visual Studio e implementar

[!INCLUDE [import publish settings](../deployment/includes/import-publish-settings-vs.md)]

## <a name="next-steps"></a>Pasos siguientes

En este tutorial, ha creado un archivo de configuración de publicación, lo ha importado a Visual Studio y ha implementado una aplicación ASP.NET en Azure App Service. Es posible que quiera obtener información general sobre opciones de publicación de Visual Studio.

> [!div class="nextstepaction"]
> [Primer vistazo a la implementación](../deployment/deploying-applications-services-and-components.md)
