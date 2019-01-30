---
title: Paseo por las características de implementación
description: Conozca las opciones para implementar aplicaciones desde Visual Studio.
ms.custom: mvc
ms.date: 06/22/2018
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
ms.openlocfilehash: 4046abd84443bd1cff6b6e618f2dfba2de5e09dd
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54974937"
---
# <a name="quickstart-first-look-at-deployment-in-visual-studio"></a>Inicio rápido: Primer vistazo a la implementación en Visual Studio

Al implementar una aplicación, un servicio o un componente, se distribuye para su instalación en otros equipos, dispositivos o servidores, o en la nube. Elija el método apropiado en Visual Studio para el tipo de implementación que necesita. (Muchos tipos de aplicaciones admiten otras herramientas de implementación, como la implementación mediante línea de comandos o NuGet, que no se tratan aquí).

Vea los inicios rápidos y los tutoriales para obtener instrucciones de implementación paso a paso. Para obtener información general sobre las opciones de implementación, vea [¿Qué opciones de publicación son las adecuadas para mí?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me).

## <a name="deploy-to-local-folder"></a>Implementar en una carpeta local

La implementación en una carpeta local se suele usar para las pruebas, o para iniciar una implementación de ensayo en la que se vaya a emplear otra herramienta para la implementación final.

- **ASP.NET**, **ASP.NET Core**, **Node.js**, **Python** y .**NET Core**: utilice la opción Publicar para implementar en una carpeta local. Las opciones concretas disponibles dependen del tipo de la aplicación. En el Explorador de soluciones, haga clic con el botón derecho en el proyecto y elija **Publicar**. (Si anteriormente ha configurado algún perfil de publicación, debe hacer clic en **Crear nuevo perfil**). Luego elija **Carpeta**. Para obtener más información, vea [Implementar en una carpeta local](quickstart-deploy-to-local-folder.md).

    ![Elección de Publicar](../deployment/media/quickstart-publish.png)

- **Runtime de Visual C++**: puede implementar el runtime de Visual C++ mediante implementación local o vinculación estática. Para obtener más información, vea [Implementar aplicaciones de escritorio nativas (Visual C++)](/cpp/ide/deploying-native-desktop-applications-visual-cpp).

## <a name="publish-to-azure"></a>Publicar en Azure

- **ASP.NET**, **ASP.NET Core**, **Python** y **Node.js**: puede usar la opción Publicar para implementar rápidamente las aplicaciones en Azure App Service o en una instancia de Azure Virtual Machines. En el Explorador de soluciones, haga clic con el botón derecho en el proyecto y seleccione **Publicar**. (Si anteriormente ha configurado algún perfil de publicación, debe hacer clic en **Crear nuevo perfil**). En el cuadro de diálogo Publicar, elija **App Service** o **Azure Virtual Machines** y luego siga los pasos de configuración.

    ![Elección de Azure App Service](../deployment/media/quickstart-publish-azure.png "Choose Azure App Service")

    En Visual Studio 2017 versión 15.7 y posteriores, puede implementar aplicaciones ASP.NET Core en **App Service para Linux**.

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

- **Runtime de Visual C++**: puede implementar el runtime de Visual C++ mediante implementación central. Para obtener más información, vea [Implementar aplicaciones de escritorio nativas (Visual C++)](/cpp/ide/deploying-native-desktop-applications-visual-cpp).

- **Escritorio de Windows**: puede publicar una aplicación de escritorio de Windows en un servidor web o en un recurso compartido de archivos de red mediante implementación de ClickOnce. A continuación, los usuarios podrán instalar la aplicación con un solo clic. Para obtener más información, vea [Implementación de una aplicación de escritorio con ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) y [Deploy a native app using ClickOnce](/cpp/ide/clickonce-deployment-for-visual-cpp-applications) (Implementar una aplicación nativa con ClickOnce).

## <a name="publish-to-microsoft-store"></a>Publicar en Microsoft Store

Desde Visual Studio, puede crear paquetes de aplicaciones para su implementación en Microsoft Store.

- **UWP**: puede empaquetar la aplicación e implementarla mediante elementos de menú. Para obtener más información, vea [Package a UWP app by using Visual Studio](/windows/uwp/packaging/packaging-uwp-apps) (Empaquetar una aplicación UWP mediante Visual Studio).

    ![Crear un paquete de aplicación](../deployment/media/feature-tour-create-app-package.jpg)

- **Escritorio de Windows**: puede implementar en Microsoft Store con Puente de dispositivo de escritorio a partir de Visual Studio 2017 versión 15.4. Para ello, empiece por crear un proyecto de paquete de aplicación de Windows. Para obtener más información, vea [Empaquetar una aplicación de escritorio para Microsoft Store (Puente de dispositivo de escritorio)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net).

    ![Puente de dispositivo de escritorio](../deployment/media/feature-tour-desktop-bridge.png)

## <a name="deploy-to-a-device-uwp"></a>Implementar en un dispositivo (UWP)

Si va a implementar una aplicación de UWP para probar en un dispositivo, vea [Run UWP apps on a remote machine in Visual Studio](../debugger/run-windows-store-apps-on-a-remote-machine.md) (Ejecutar aplicaciones de UWP en un equipo remoto en Visual Studio).

## <a name="create-an-installer-package-windows-client"></a>Crear un paquete de instalador (cliente de Windows)

Si necesita una instalación más compleja de una aplicación de escritorio de lo que [ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) puede proporcionar, puede crear un paquete de instalador, un proyecto de instalación o un arranque personalizado.

- Se puede crear un instalador de WiX basado en MSI mediante [WiX Toolset Visual Studio 2017 Extension](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).

- Se puede usar [InstallShield](https://www.flexerasoftware.com/producer/products/software-installation/installshield-software-installer/tab/requirements) de Flexera Software con Visual Studio 2017 (Community Edition no admitida). Tenga en cuenta que InstallShield Limited Edition ya no se incluye con Visual Studio y no se admite en Visual Studio 2017; póngase en contacto con [Flexera Software](http://learn.flexerasoftware.com/content/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio) para consultar sobre su disponibilidad futura.

- Si quiere crear un proyecto de instalación (vdproj), instale la extensión [Visual Studio 2017 Installer Projects](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.MicrosoftVisualStudio2017InstallerProjects#overview).

- Puede instalar los componentes de requisitos previos para las aplicaciones de escritorio si configura un instalador genérico, lo que se conoce como programa previo. Para obtener más información, vea [Application Deployment Prerequisites](../deployment/application-deployment-prerequisites.md) (Requisitos previos de implementación de aplicaciones).

## <a name="deploy-to-test-lab"></a>Implementar en Test Lab

Puede habilitar un desarrollo y pruebas más sofisticados si implementa las aplicaciones en entornos virtuales. Para obtener más información, vea [Probar en un entorno de laboratorio](../test/lab-management/using-a-lab-environment-for-your-application-lifecycle.md).

## <a name="devops-deployment"></a>Implementación de DevOps

En un entorno de equipo, puede usar Azure Pipelines para habilitar la implementación continua de la aplicación. Para obtener más información, vea [Azure Pipelines](/azure/devops/pipelines/index?view=vsts) e [Implementar en Azure](/azure/devops/deploy-azure/index?view=vsts).

## <a name="deployment-for-other-app-types"></a>Implementación de otros tipos de aplicaciones

| Tipo de aplicación | Escenario de implementación | Vínculo |
| --- | --- | --- |
| **Aplicación de Office** | Puede publicar un complemento de Office desde Visual Studio. | [Implementar y publicar un complemento de Office](https://dev.office.com/docs/add-ins/publish/publish) |
| **Servicio OData o WCF** | Otras aplicaciones pueden usar los servicios RIA de WCF que se implementen en un servidor web. | [Desarrollo e implementación de WCF Data Services](/dotnet/framework/data/wcf/developing-and-deploying-wcf-data-services) |
| **LightSwitch** | LightSwitch ya no se admite en Visual Studio 2017, pero todavía se puede implementar desde Visual Studio 2015 y versiones anteriores. | [Implementar aplicaciones LightSwitch](https://msdn.microsoft.com/Library/4818d933-295c-4ecc-9148-7ad9ca28dcdb) |

## <a name="next-steps"></a>Pasos siguientes

En este tutorial he echado un vistazo rápido a las opciones de implementación de diferentes aplicaciones.

> [!div class="nextstepaction"]
> [¿Qué opciones de publicación son las adecuadas para mí?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me)
