---
title: Publicar en IIS mediante la importación de la configuración de publicación
description: Creación e importación de un perfil de publicación para implementar una aplicación desde Visual Studio en IIS
ms.date: 05/06/2020
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b18d1b123e32807575ac2c6601166891d6c25be
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2020
ms.locfileid: "84183306"
---
# <a name="publish-an-application-to-iis-by-importing-publish-settings-in-visual-studio"></a>Publicar una aplicación en IIS mediante la importación de la configuración de publicación en Visual Studio

Puede usar la herramienta **Publicar** para importar la configuración de publicación y después implementar la aplicación. En este artículo, se usa la configuración de publicación de IIS, pero puede usar los mismos pasos para importar la configuración de publicación para [Azure App Service](../deployment/tutorial-import-publish-settings-azure.md). En algunos escenarios, el uso de un perfil de configuración de publicación puede ser más rápido que configurar manualmente la implementación en IIS para cada instalación de Visual Studio.

Estos pasos se aplican a aplicaciones ASP.NET, ASP.NET Core y .NET Core en Visual Studio.

En este tutorial va a:

> [!div class="checklist"]
> * Configurar IIS para que pueda generar un archivo de configuración de publicación
> * Crear un archivo de configuración de publicación
> * Importar el archivo de configuración de publicación a Visual Studio
> * Implementar la aplicación en IIS

Un archivo de configuración de publicación ( *\*.publishsettings*) es diferente de un perfil de publicación ( *\*.pubxml*) creado en Visual Studio. Un archivo de configuración de publicación se crea mediante IIS o Azure App Service, o puede crearse manualmente y después importarse en Visual Studio.

> [!NOTE]
> Si tan solo necesita copiar un perfil de publicación de Visual Studio (archivo\*.pubxml) de una instalación de Visual Studio en otra, puede encontrar el perfil de publicación, *\<profilename\>.pubxml*, en la carpeta *\\<nombredeproyecto\>\Properties\PublishProfiles* correspondiente a los tipos de proyecto administrados. Para sitios web, busque en la carpeta *\App_Data*. Los perfiles de publicación son archivos XML de MSBuild.

## <a name="prerequisites"></a>Requisitos previos

::: moniker range=">=vs-2019"

* Debe tener instalado Visual Studio 2019 y la carga de trabajo **Desarrollo web y ASP.NET**.

    Si todavía no ha instalado Visual Studio, vaya a la página de  [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/)  para instalarlo de forma gratuita.
::: moniker-end

::: moniker range="vs-2017"

* Debe tener instalado Visual Studio 2017 y la carga de trabajo **Desarrollo web y ASP.NET**.

    Si todavía no ha instalado Visual Studio, vaya a la página de  [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/)  para instalarlo de forma gratuita.
::: moniker-end

* En el servidor, debe ejecutar Windows Server 2012, Windows Server 2016 o Windows Server 2019, y tener el [rol de servidor web de IIS](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) configurado correctamente (es necesario para generar el archivo de configuración de publicación [ *\*.publishsettings*]). También se debe instalar ASP.NET 4.5 o ASP.NET Core en el servidor. Para configurar ASP.NET 4.5, vea [IIS 8.0 Using ASP.NET 3.5 and ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) (IIS 8.0 con ASP.NET 3.5 y ASP.NET 4.5). Para configurar ASP.NET Core, vea [Hospedaje de ASP.NET Core en Windows con IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration). En ASP.NET Core, asegúrese de configurar el grupo de aplicaciones para que use **Sin código administrado**, tal y como se describe en el artículo.

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Crear un nuevo proyecto de ASP.NET en Visual Studio

1. En el equipo con Visual Studio, cree un proyecto.

    Elija la plantilla correcta. En este ejemplo, elija **Aplicación web ASP.NET (.NET Framework)** o (solo para C#) **Aplicación web ASP.NET Core** y haga clic en **Aceptar**.

    Si no ve las plantillas de proyecto especificadas, haga clic en el vínculo **Abrir el instalador de Visual Studio** en el panel izquierdo del cuadro de diálogo **Nuevo proyecto**. Se iniciará el Instalador de Visual Studio. Instale la carga de trabajo **ASP.NET y desarrollo web**.

    La plantilla de proyecto que elija (ASP.NET o ASP.NET Core) debe coincidir con la versión de ASP.NET instalada en el servidor web.

1. Elija **MVC** (.NET Framework) o **Aplicación web (Modelo-Vista-Controlador)** (para .NET Core), y asegúrese de que la opción **Sin autenticación** está seleccionada y después haga clic en **Aceptar**.

1. Escriba un nombre como **MyWebApp** y haga clic en **Aceptar**.

    Visual Studio crea el proyecto.

1. Elija **Compilar** > **Compilar solución** para compilar el proyecto.

## <a name="install-and-configure-web-deploy-on-windows-server"></a>Instalar y configurar Web Deploy o Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

## <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Crear el archivo de configuración de publicación en IIS en Windows Server

[!INCLUDE [create-publish-settings-iis](../deployment/includes/create-publish-settings-iis.md)]

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importar la configuración de publicación a Visual Studio e implementar

[!INCLUDE [import-publish-settings](../deployment/includes/import-publish-settings-vs.md)]

Después de que se implemente la aplicación correctamente, debería iniciarse automáticamente. Si no se inicia desde Visual Studio, inicie la aplicación en IIS. Para ASP.NET Core, deberá asegurarse de que el campo Grupo de aplicaciones para el **DefaultAppPool** está establecido en **Sin código administrado**.

## <a name="next-steps"></a>Pasos siguientes

En este tutorial, creó un archivo de configuración de publicación, lo importó en Visual Studio e implementó una aplicación ASP.NET en IIS. Es posible que desee obtener información general de otras opciones de publicación en Visual Studio.

> [!div class="nextstepaction"]
> [Primer vistazo a la implementación](../deployment/deploying-applications-services-and-components.md)
