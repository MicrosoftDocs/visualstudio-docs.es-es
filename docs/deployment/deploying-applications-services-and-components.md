---
title: Primer vistazo a la implementación
description: Conozca las opciones para implementar aplicaciones desde Visual Studio.
ms.custom: mvc
ms.date: 01/29/2019
ms.topic: quickstart
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- .NET applications, deploying
- components [Visual Studio], deploying
- installers
- publishing
- deploying applications [Visual Studio]
- deploying applications [Visual Studio], about deploying applications
- components [.NET Framework], deploying
ms.assetid: 63fcdd5b-2e54-4210-9038-65bc23167725
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf78e17d4d804c94392da045a90c98869319d185
ms.sourcegitcommit: fe212f8960d7882a1b0fdae9e22f008996aacf3c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222613"
---
# <a name="first-look-at-deployment-in-visual-studio"></a>Primer vistazo a la implementación en Visual Studio

Al implementar una aplicación, un servicio o un componente, se distribuye para su instalación en otros equipos, dispositivos o servidores, o en la nube. Elija el método apropiado en Visual Studio para el tipo de implementación que necesita. (Muchos tipos de aplicaciones admiten otras herramientas de implementación, como la implementación mediante línea de comandos o NuGet, que no se tratan aquí).

Vea los inicios rápidos y los tutoriales para obtener instrucciones de implementación paso a paso. Para obtener información general sobre las opciones de implementación, vea [¿Qué opciones de publicación son las adecuadas para mí?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me).

## <a name="deploy-to-local-folder"></a>Implementar en una carpeta local

La implementación en una carpeta local se suele usar para las pruebas, o para iniciar una implementación de ensayo en la que se vaya a emplear otra herramienta para la implementación final.

- **ASP.NET**, **ASP.NET Core**, **Node.js**, **Python** y .**NET Core**: utilice la opción Publicar para implementar en una carpeta local. Las opciones concretas disponibles dependen del tipo de la aplicación. En el Explorador de soluciones, haga clic con el botón derecho en el proyecto y elija **Publicar**. (Si anteriormente no ha configurado ningún perfil de publicación, debe hacer clic en **Crear nuevo perfil**). Luego elija **Carpeta**. Para obtener más información, vea [Implementar en una carpeta local](quickstart-deploy-to-local-folder.md).

    ![Elección de Publicar](../deployment/media/quickstart-publish.png)

- **Escritorio de Windows**: puede publicar una aplicación de escritorio de Windows en una carpeta mediante la implementación de ClickOnce. A continuación, los usuarios podrán instalar la aplicación con un solo clic. Para más información, vea [Implementación de una aplicación de escritorio con ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# y Visual Basic). Para C++ y CLR, vea [Implementación de ClickOnce para aplicaciones de Visual C++](/cpp/windows/clickonce-deployment-for-visual-cpp-applications), o bien, para C y C ++, vea [Implementación de una aplicación de Visual C++ mediante un proyecto de instalación](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="publish-to-azure"></a>Publicar en Azure

- **ASP.NET**, **ASP.NET Core**, **Python** y **Node.js**: Publique en Azure App Service o Azure App Service para Linux (con contenedores) mediante uno de los métodos siguientes.

  - Para la implementación continua (o automática) de aplicaciones, use Azure DevOps con [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/get-started-yaml?view=azdevops).

  - Para la implementación de un solo uso (o manual) de aplicaciones, use la herramienta de **publicación** de Visual Studio.

  Para una implementación que proporcione una configuración más personalizada del servidor, también puede usar la herramienta de **publicación** para implementar aplicaciones en una máquina virtual de Azure.

  Para usar la herramienta de **publicación**, haga clic con el botón derecho en el proyecto en el Explorador de soluciones y seleccione **Publicar**. (Si anteriormente ha configurado algún perfil de publicación, debe hacer clic en **Crear nuevo perfil**). En el cuadro de diálogo Publicar, elija **App Service** o **Azure Virtual Machines** y luego siga los pasos de configuración.

  ![Elección de Azure App Service](../deployment/media/quickstart-publish-azure.png "Elección Azure App Service")

  A partir de Visual Studio 2017 versión 15.7, puede implementar aplicaciones ASP.NET Core en **App Service para Linux**.

  En el caso de las aplicaciones de Python, vea también [Python: Publicación en Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json).

  Para obtener una introducción rápida, vea [Publicar en Azure](quickstart-deploy-to-azure.md) y [Publicar en Linux](quickstart-deploy-to-linux.md). Además, vea [Publicar una aplicación de ASP.NET Core en Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). Para implementar mediante Git, vea [Implementación continua en Azure con Visual Studio y Git con ASP.NET Core](/aspnet/core/publishing/azure-continuous-deployment).

  Para obtener información sobre la importación de un perfil de publicación de Azure App Service en Visual Studio, vea [Importar una configuración de publicación e implementar en Azure](../deployment/tutorial-import-publish-settings-azure.md).

  > [!NOTE]
  > Si aún no tiene una cuenta de Azure, puede [registrarse aquí](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio).

## <a name="publish-to-web-or-deploy-to-network-share"></a>Publicar en Internet o implementar en un recurso compartido de red

- **ASP.NET**, **ASP.NET Core**, **Node.js** y **Python**: puede usar la opción Publicar para implementar en un sitio web mediante FTP o Web Deploy. Para obtener más información, vea [Implementar en un sitio web](quickstart-deploy-to-a-web-site.md).

    En el Explorador de soluciones, haga clic con el botón derecho en el proyecto y seleccione **Publicar**. (Si anteriormente ha configurado algún perfil de publicación, debe hacer clic en **Crear nuevo perfil**). En la herramienta Publicar, elija la opción que quiera y siga los pasos de configuración.

    ![Elección de IIS, FTP, etc.](../deployment/media/quickstart-publish-iis-ftp.png)

    Para obtener información sobre la importación de un perfil de publicación en Visual Studio, vea [Importación de una configuración de publicación e implementación en IIS](../deployment/tutorial-import-publish-settings-iis.md).

    También puede implementar aplicaciones y servicios ASP.NET de más maneras. Para obtener más información, vea [Deploying ASP.NET web applications and services](http://www.asp.net/aspnet/overview/deployment) (Implementación de aplicaciones y servicios web ASP.NET).

- **Escritorio de Windows**: puede publicar una aplicación de escritorio de Windows en un servidor web o en un recurso compartido de archivos de red mediante implementación de ClickOnce. A continuación, los usuarios podrán instalar la aplicación con un solo clic. Para más información, vea [Implementación de una aplicación de escritorio con ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# y Visual Basic). Para C++ y CLR, vea [Implementación de ClickOnce para aplicaciones de Visual C++](/cpp/windows/clickonce-deployment-for-visual-cpp-applications), o bien, para C y C ++, vea [Implementación de una aplicación de Visual C++ mediante un proyecto de instalación](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="publish-to-microsoft-store"></a>Publicar en Microsoft Store

Desde Visual Studio, puede crear paquetes de aplicaciones para su implementación en Microsoft Store.

- **UWP**: puede empaquetar la aplicación e implementarla mediante elementos de menú. Para obtener más información, vea [Package a UWP app by using Visual Studio](/windows/uwp/packaging/packaging-uwp-apps) (Empaquetar una aplicación UWP mediante Visual Studio).

    ![Crear un paquete de aplicación](../deployment/media/feature-tour-create-app-package.jpg)

- **Escritorio de Windows**: puede implementar en Microsoft Store con Puente de dispositivo de escritorio a partir de Visual Studio 2017 versión 15.4. Para ello, empiece por crear un proyecto de paquete de aplicación de Windows. Para obtener más información, vea [Empaquetar una aplicación de escritorio para Microsoft Store (Puente de dispositivo de escritorio)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net).

    ![Puente de dispositivo de escritorio](../deployment/media/feature-tour-desktop-bridge.png)

## <a name="deploy-net-packages-to-nugetorg"></a>Implementación de paquetes .NET en NuGet.org

Para implementar código agrupado en "paquetes" que contengan código compilado (como archivos DLL) junto con otro contenido necesario en los proyectos que consumen estos paquetes, puede usar Visual Studio para crear el paquete NuGet y una herramienta de la CLI para emitir el comando de implementación final.

- [Creación y publicación de un paquete .NET Standard](/nuget/quickstart/create-and-publish-a-package-using-visual-studio)
- [Creación y publicación de un paquete de .NET Framework](/nuget/quickstart/create-and-publish-a-package-using-visual-studio-net-framework)

## <a name="deploy-to-a-device-uwp"></a>Implementar en un dispositivo (UWP)

Si va a implementar una aplicación de UWP para probar en un dispositivo, vea [Run UWP apps on a remote machine in Visual Studio](../debugger/run-windows-store-apps-on-a-remote-machine.md) (Ejecutar aplicaciones de UWP en un equipo remoto en Visual Studio).

## <a name="create-an-installer-package-windows-desktop"></a>Creación de un paquete de instalador (escritorio de Windows)

Si necesita una instalación más compleja de una aplicación de escritorio de lo que [ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) puede proporcionar, puede crear un paquete de Windows Installer (un archivo de instalación MSI o EXE), o bien un programa previo personalizado.

- Se puede crear un paquete de instalador basado en MSI mediante la [extensión WiX Toolset](https://marketplace.visualstudio.com/items?itemName=WixToolset.WiXToolset). Se trata de un conjunto de herramientas de línea de comandos.

   ::: moniker range=">=vs-2019"
   En Visual Studio 2019, obtenga la [extensión WiX Toolset de Visual Studio 2019](https://marketplace.visualstudio.com/items?itemName=WixToolset.WixToolsetVisualStudio2019Extension).
   ::: moniker-end

- Se puede crear un paquete de instalador EXE o MSI mediante [InstallShield](https://www.flexerasoftware.com/producer/products/software-installation/installshield-software-installer/tab/requirements) de Flexera Software. InstallShield se puede usar con Visual Studio 2017 y versiones posteriores (no se admite Community Edition). Tenga en cuenta que InstallShield Limited Edition ya no se incluye con Visual Studio y no se admite en Visual Studio 2017 y versiones posteriores; póngase en contacto con [Flexera Software](http://learn.flexerasoftware.com/content/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio) para consultar sobre su disponibilidad futura.

- Un paquete de instalador EXE o MSI se puede crear mediante un proyecto de instalación (vdproj). Para usar esta opción, instale la [extensión de proyectos del Instalador de Visual Studio](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.MicrosoftVisualStudio2017InstallerProjects#overview).

- También puede instalar componentes de requisitos previos para las aplicaciones de escritorio si configura un instalador genérico, lo que se conoce como programa previo. Para obtener más información, vea [Application Deployment Prerequisites](../deployment/application-deployment-prerequisites.md) (Requisitos previos de implementación de aplicaciones).

## <a name="deploy-to-test-lab"></a>Implementar en Test Lab

Puede habilitar un desarrollo y pruebas más sofisticados si implementa las aplicaciones en entornos virtuales. Para obtener más información, vea [Probar en un entorno de laboratorio](../test/lab-management/using-a-lab-environment-for-your-application-lifecycle.md).

## <a name="continuous-deployment"></a>Implementación continua

Puede usar Azure Pipelines para habilitar la implementación continua de la aplicación. Para obtener más información, vea [Azure Pipelines](/azure/devops/pipelines/index?view=vsts) e [Implementar en Azure](/azure/devops/deploy-azure/index?view=vsts).

## <a name="deploy-a-sql-database"></a>Implementación de una base de datos SQL

- [Cambiar la plataforma de destino y publicar un proyecto de base de datos [SQL Server Data Tools (SSDT)]](/sql/ssdt/how-to-change-target-platform-and-publish-a-database-project)

- [Crear un proyecto de Analysis Services (SSAS)](/sql/analysis-services/multidimensional-tutorial/lesson-2-5-deploying-an-analysis-services-project)

- [Implementar paquetes y proyectos de Integration Services (SSIS)](/sql/integration-services/packages/deploy-integration-services-ssis-projects-and-packages)

- [Compilar e implementar una base de datos local](/sql/ssdt/how-to-build-and-deploy-to-a-local-database)

## <a name="deployment-for-other-app-types"></a>Implementación de otros tipos de aplicaciones

| Tipo de aplicación | Escenario de implementación | Link |
| --- | --- | --- |
| **Aplicación de Office** | Puede publicar un complemento de Office desde Visual Studio. | [Implementar y publicar un complemento de Office](https://dev.office.com/docs/add-ins/publish/publish) |
| **Servicio OData o WCF** | Otras aplicaciones pueden usar los servicios RIA de WCF que se implementen en un servidor web. | [Desarrollo e implementación de WCF Data Services](/dotnet/framework/data/wcf/developing-and-deploying-wcf-data-services) |
| **LightSwitch** | LightSwitch ya no se admite a partir de Visual Studio 2017, pero todavía se puede implementar desde Visual Studio 2015 y versiones anteriores. | [Implementar aplicaciones LightSwitch](https://msdn.microsoft.com/Library/4818d933-295c-4ecc-9148-7ad9ca28dcdb) |

## <a name="next-steps"></a>Pasos siguientes

En este tutorial he echado un vistazo rápido a las opciones de implementación de diferentes aplicaciones.

> [!div class="nextstepaction"]
> [¿Qué opciones de publicación son las adecuadas para mí?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me)
