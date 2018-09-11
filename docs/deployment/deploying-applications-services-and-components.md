---
title: Guía de características de implementación
description: Obtenga información acerca de las opciones para implementar aplicaciones desde Visual Studio.
ms.custom: mvc
ms.date: 06/22/2018
ms.technology: vs-ide-deployment
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 83b6449d3f9fb41280d9e0b051c5baf3edbf5a66
ms.sourcegitcommit: 28909340cd0a0d7cb5e1fd29cbd37e726d832631
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44320558"
---
# <a name="quickstart-first-look-at-deployment-in-visual-studio"></a>Inicio rápido: Primer vistazo a la implementación en Visual Studio

Mediante la implementación de una aplicación, servicio o componente, se distribuye para su instalación en otros equipos, dispositivos o servidores, o en la nube. Elija el método apropiado en Visual Studio para el tipo de implementación que necesita. (Muchos tipos de aplicaciones admiten otras herramientas de implementación, como la implementación de línea de comandos o a NuGet que no se describen aquí).

Consulte las guías rápidas y tutoriales para obtener instrucciones paso a paso de implementación. Para obtener información general de las opciones de implementación, consulte [qué opciones de publicación son adecuadas para mí?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me).

## <a name="deploy-to-local-folder"></a>Implementar en una carpeta local

Implementación en una carpeta local se utiliza normalmente para las pruebas, o para iniciar una implementación de ensayo en el que se utiliza otra herramienta para la implementación final.

- **ASP.NET**, **ASP.NET Core**, **Node.js**, **Python**, y. **NET Core**: usar la herramienta de publicación para implementar en una carpeta local. Las opciones disponibles dependen de su tipo de aplicación. En el Explorador de soluciones, haga clic en el proyecto y elija **publicar**. (Si anteriormente ha configurado ningún perfil de publicación, debe hacer clic **crear nuevo perfil**.) A continuación, elija **carpeta**. Para obtener más información, consulte [implementar en una carpeta local](quickstart-deploy-to-local-folder.md).

    ![Elija publicar](../deployment/media/quickstart-publish.png)

- **El tiempo de ejecución Visual C++**: puede implementar el runtime de Visual C++ mediante la implementación local o vinculación estática. Para obtener más información, consulte [implementar aplicaciones de escritorio nativas (Visual C++)](/cpp/ide/deploying-native-desktop-applications-visual-cpp).

## <a name="publish-to-azure"></a>Publicar en Azure

- **ASP.NET**, **ASP.NET Core**, **Python**, y **Node.js**: puede usar la herramienta de publicación para implementar rápidamente las aplicaciones en Azure App Service o a una Virtual de Azure Máquina. En el Explorador de soluciones, haga clic con el botón derecho en el proyecto y seleccione **Publicar**. (Si anteriormente ha configurado ningún perfil de publicación, debe hacer clic **crear nuevo perfil**.) En el cuadro de diálogo Publicar, elija **App Service** o **Azure Virtual Machines**y, a continuación, siga los pasos de configuración.

    ![Elija Azure App Service](../deployment/media/quickstart-publish-azure.png "elegir Azure App Service")

    En Visual Studio 2017 versión 15.7 y versiones posterior, donde puede implementar aplicaciones ASP.NET Core **App Service para Linux**.

    Para las aplicaciones de Python, consulte también [Python - publicar en Azure App Service](/visualstudio/python/publishing-python-web-applications-to-azure-from-visual-studio?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json).

    Para obtener una introducción rápida, consulte [publicar en Azure](quickstart-deploy-to-azure.md) y [publicar en Linux](quickstart-deploy-to-linux.md). Consulte también [publicar una aplicación ASP.NET Core en Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). Para implementar mediante Git, consulte [implementación continua de ASP.NET Core en Azure con Git](/aspnet/core/publishing/azure-continuous-deployment).

    Para obtener información sobre cómo importar un perfil de publicación de Azure App Service en Visual Studio, consulte [importar configuración de publicación e implementación en Azure](../deployment/tutorial-import-publish-settings-azure.md).

    > [!NOTE]
    > Si no dispone de una cuenta de Azure, puede [Regístrese aquí](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio).

## <a name="publish-to-web-or-deploy-to-network-share"></a>Publicar en Web o implementar en el recurso compartido de red

- **ASP.NET**, **ASP.NET Core**, **Node.js**, y **Python**: puede usar la herramienta de publicación para implementar en un sitio Web mediante FTP o Web Deploy. Para obtener más información, consulte [implementar en un sitio web](quickstart-deploy-to-a-web-site.md).

    En el Explorador de soluciones, haga clic con el botón derecho en el proyecto y seleccione **Publicar**. (Si anteriormente ha configurado ningún perfil de publicación, debe hacer clic **crear nuevo perfil**.) En la herramienta de publicación, elija la opción que desee y siga los pasos de configuración.

    ![Elija IIS, FTP, etcetera.](../deployment/media/quickstart-publish-iis-ftp.png)

    Para obtener información sobre cómo importar un perfil de publicación en Visual Studio, consulte [importar configuración de publicación e implementación en IIS](../deployment/tutorial-import-publish-settings-iis.md).

    También puede implementar aplicaciones ASP.NET y servicios en un número de otras maneras. Para obtener más información, consulte [ASP.NET de la implementación de aplicaciones y servicios web](http://www.asp.net/aspnet/overview/deployment).

- **El tiempo de ejecución Visual C++**: puede implementar el runtime de Visual C++ mediante la implementación central. Para obtener más información, consulte [implementar aplicaciones de escritorio nativas (Visual C++)](/cpp/ide/deploying-native-desktop-applications-visual-cpp).

- **Escritorio de Windows** puede publicar una aplicación de escritorio de Windows a un servidor web o un recurso compartido de red mediante la implementación de ClickOnce. A continuación, los usuarios podrán instalar la aplicación con un solo clic. Para obtener más información, consulte [implementar una aplicación de escritorio con ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) y [implementar una aplicación nativa con ClickOnce](/cpp/ide/clickonce-deployment-for-visual-cpp-applications).

## <a name="publish-to-microsoft-store"></a>Publicar en Microsoft Store

Desde Visual Studio, puede crear paquetes de aplicaciones para su implementación en Microsoft Store.

- **UWP**: se puede empaquetar la aplicación e implementarlo mediante los elementos de menú. Para obtener más información, consulte [empaquetar una aplicación para UWP con Visual Studio](/windows/uwp/packaging/packaging-uwp-apps).

    ![Crear un paquete de aplicación](../deployment/media/feature-tour-create-app-package.jpg)

- **Escritorio de Windows**: puede implementar en la Microsoft Store con el puente de escritorio a partir de Visual Studio 2017 versión 15.4. Para ello, empiece por crear un proyecto de empaquetado de aplicaciones de Windows. Para obtener más información, consulte [empaquetar una aplicación de escritorio de Microsoft Store (puente de escritorio)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net).

    ![Puente de escritorio](../deployment/media/feature-tour-desktop-bridge.png)

## <a name="deploy-to-a-device-uwp"></a>Implementar en un dispositivo (UWP)

Si va a implementar una aplicación para UWP para pruebas en un dispositivo, consulte [ejecutar aplicaciones para UWP en un equipo remoto en Visual Studio](../debugger/run-windows-store-apps-on-a-remote-machine.md).

## <a name="create-an-installer-package-windows-client"></a>Crear un paquete de instalador (cliente de Windows)

Si se requiere más de una instalación compleja de una aplicación de escritorio que [ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) puede proporcionar, puede crear un paquete de instalador, un proyecto de instalación o un arranque personalizado.

- Se puede crear un instalador de WiX basada en MSI mediante el [WiX conjunto de herramientas de Visual Studio 2017 extensión](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).

- [InstallShield](https://www.flexerasoftware.com/producer/products/software-installation/installshield-software-installer/tab/requirements) de Flexera Software puede usar con Visual Studio 2017 (Community Edition no admite). Tenga en cuenta que InstallShield Limited Edition ya no se incluye con Visual Studio y no se admite en Visual Studio 2017; Póngase en contacto con [Flexera Software](http://learn.flexerasoftware.com/content/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio) acerca de la disponibilidad futura.

- Si desea crear un proyecto de instalación (vdproj), instale el [extensión de proyectos del instalador de Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.MicrosoftVisualStudio2017InstallerProjects#overview).

- Puede instalar los componentes necesarios para las aplicaciones de escritorio si configura a un instalador genérico, que se conoce como un programa previo. Para obtener más información, consulte [requisitos previos de implementación de aplicación](../deployment/application-deployment-prerequisites.md).

## <a name="deploy-to-test-lab"></a>Implementar para el laboratorio de pruebas

Puede habilitar el desarrollo y pruebas mediante la implementación de las aplicaciones en entornos virtuales más sofisticados. Para obtener más información, consulte [pruebas en un entorno de laboratorio](../test/lab-management/using-a-lab-environment-for-your-application-lifecycle.md).

## <a name="devops-deployment"></a>Implementación de DevOps

En un entorno de equipo, puede utilizar las canalizaciones de Azure para habilitar la implementación continua de la aplicación. Para obtener más información, consulte [canalizaciones de Azure](/azure/devops/pipelines/index?view=vsts) y [implementar en Azure](/azure/devops/deploy-azure/index?view=vsts).

## <a name="deployment-for-other-app-types"></a>Implementación de otros tipos de aplicaciones

| Tipo de aplicación | Escenario de implementación | Vínculo |
| --- | --- | --- |
| **Aplicación de Office** | Puede publicar un complemento de Office en Visual Studio. | [Implementar y publicar el complemento de Office](https://dev.office.com/docs/add-ins/publish/publish) |
| **Servicio WCF o OData**  | Otras aplicaciones pueden utilizar los servicios de RIA de WCF que se implementen en un servidor web. | [Desarrollar e implementar WCF Data Services](/dotnet/framework/data/wcf/developing-and-deploying-wcf-data-services) |
| **LightSwitch** | LightSwitch ya no se admite en Visual Studio 2017, pero todavía se puede implementar desde Visual Studio 2015 y versiones anteriores. | [Implementación de aplicaciones de LightSwitch](https://msdn.microsoft.com/Library/4818d933-295c-4ecc-9148-7ad9ca28dcdb) |

## <a name="next-steps"></a>Pasos siguientes

En este tutorial, se tardó un vistazo rápido a opciones de implementación para diferentes aplicaciones.

> [!div class="nextstepaction"]
> [¿Qué opciones de publicación son adecuadas para mí?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me)
