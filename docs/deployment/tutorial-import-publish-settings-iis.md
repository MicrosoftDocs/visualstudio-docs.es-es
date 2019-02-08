---
title: Publicar en IIS mediante la importación de la configuración de publicación
description: Creación e importación de un perfil de publicación para implementar una aplicación desde Visual Studio en IIS
ms.date: 01/31/2019
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b38f9d951be37619c84095c379879e1acd51cf7b
ms.sourcegitcommit: 0f7411c1a47d996907a028e920b73b53c2098c9f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/04/2019
ms.locfileid: "55690455"
---
# <a name="publish-an-application-to-iis-by-importing-publish-settings-in-visual-studio"></a>Publicar una aplicación en IIS mediante la importación de la configuración de publicación en Visual Studio

Puede usar la herramienta **Publicar** para importar la configuración de publicación y después implementar la aplicación. En este artículo, se usa la configuración de publicación de IIS, pero puede usar los mismos pasos para importar la configuración de publicación para [Azure App Service](../deployment/tutorial-import-publish-settings-azure.md). En algunos escenarios, el uso de un perfil de configuración de publicación puede ser más rápido que configurar manualmente la implementación en IIS para cada instalación de Visual Studio.

Estos pasos se aplican a las aplicaciones de ASP.NET, ASP.NET Core y .NET Core en Visual Studio. Estos pasos corresponden a Visual Studio 2017 versión 15.6.

En este tutorial va a:

> [!div class="checklist"]
> * Configurar IIS para que pueda generar un archivo de configuración de publicación
> * Crear un archivo de configuración de publicación
> * Importar el archivo de configuración de publicación a Visual Studio
> * Implementar la aplicación en IIS

Un archivo de configuración de publicación (*\*.publishsettings*) es diferente de un perfil de publicación (*\*.pubxml*) creado en Visual Studio. Un archivo de configuración de publicación se crea mediante IIS o Azure App Service, o puede crearse manualmente y después importarse en Visual Studio.

> [!NOTE]
> Si desea copiar un perfil de publicación de Visual Studio (\*archivo .pubxml) de una instalación de Visual Studio a otra, puede encontrar el perfil de publicación, *\<nombredeperfil\>.pubxml*, en la carpeta *\\<nombredeproyecto\>\Properties\PublishProfiles* para los tipos de proyecto administrados. Para los sitios web, busque en la carpeta *\App_Data*. Los perfiles de publicación son archivos XML de MSBuild.

## <a name="prerequisites"></a>Requisitos previos

* En el equipo de desarrollo, debe tener instalado Visual Studio 2017 y la carga de trabajo **Desarrollo web y ASP.NET**.

    Si todavía no ha instalado Visual Studio, vaya a la página de  [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)  para instalarlo de forma gratuita.

* En el servidor, debe ejecutar Windows Server 2012 o Windows Server 2016, y tener el [rol de servidor web de IIS](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) configurado correctamente (necesario para generar el archivo de configuración de publicación (*\*.publishsettings*)). También se debe instalar ASP.NET 4.5 o ASP.NET Core en el servidor. Para configurar ASP.NET 4.5, vea [IIS 8.0 Using ASP.NET 3.5 and ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) (IIS 8.0 con ASP.NET 3.5 y ASP.NET 4.5). Para configurar ASP.NET Core, vea [Hospedaje de ASP.NET Core en Windows con IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration). 

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Crear un nuevo proyecto de ASP.NET en Visual Studio

1. En el equipo con Visual Studio, elija **Archivo** > **Nuevo proyecto**.

1. En **Visual C#** o **Visual Basic**, elija **Web** y, en el panel central, elija **Aplicación web ASP.NET (.NET Framework)** o (solo para C#) **Aplicación web ASP.NET Core** y haga clic en **Aceptar**.

    Si no ve las plantillas de proyecto especificadas, haga clic en el vínculo **Abrir el instalador de Visual Studio** en el panel izquierdo del cuadro de diálogo **Nuevo proyecto**. Se iniciará el Instalador de Visual Studio. Instale la carga de trabajo **ASP.NET y desarrollo web**.

    La plantilla de proyecto que elija (ASP.NET o ASP.NET Core) debe coincidir con el 

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
