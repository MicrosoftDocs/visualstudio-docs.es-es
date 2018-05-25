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
ms.openlocfilehash: 907fecd348dba46f6d3375d2d994b04ec1cf1eb5
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/24/2018
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

* Debe tener instalado de Visual Studio 2017 y **ASP.NET** y **.NET Framework** cargas de trabajo de desarrollo. Para una aplicación .NET Core, también necesitará el **.NET Core** carga de trabajo.

    Si todavía no tiene instalado Visual Studio, puede descargarlo de forma gratuita en [esta página](http://www.visualstudio.com).

* Para generar el archivo de configuración de publicación de IIS, debe tener un equipo que ejecuta Windows Server 2012 o Windows Server 2016, y debe tener el rol de servidor Web de IIS configurado correctamente. También debe tener instalado ASP.NET 4.5 o ASP.NET Core. Para ASP.NET Core, vea [publicar en IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration). Para ASP.NET 4.5, consulte [IIS 8.0 utilizando ASP.NET 3.5 y 4.5 de ASP.NET](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

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

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importar la configuración de publicación en Visual Studio e implementar

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Después de que la aplicación se implementa correctamente, debe iniciarse automáticamente. Si no se inicia desde Visual Studio, inicie la aplicación en IIS. Para ASP.NET Core, debe asegurarse de que el grupo de aplicaciones de campo para el **DefaultAppPool** está establecido en **sin código administrado**.

## <a name="next-steps"></a>Pasos siguientes

En este tutorial, creó un archivo de configuración de publicación, había importado en Visual Studio e implementa una aplicación ASP.NET en IIS.

> [!div class="nextstepaction"]
> [Primer vistazo a la implementación](../deployment/deploying-applications-services-and-components.md)
