---
title: "Información general de implementación - Visual Studio | Documentos de Microsoft"
ms.custom: 
ms.date: 11/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "33"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 30261fea83870b5bdfce11a25969207aad260ee4
ms.sourcegitcommit: 64c7682ec3a2cbea684e716803398d4278b591d1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2017
---
# <a name="deployment-overview-in-visual-studio"></a>Información general de la implementación en Visual Studio

Al implementar una aplicación, servicio o componente, se distribuye para su instalación en otros equipos, dispositivos, servidores o en la nube. Elija el método apropiado en Visual Studio para el tipo de implementación que necesita. (Muchos tipos de aplicación admiten otras herramientas de implementación como la implementación de línea de comandos o NuGet que no se describen aquí).

Vea los tutoriales para obtener instrucciones paso a paso.

### <a name="deploy-to-local-folder"></a>Implementar en la carpeta local

- **ASP.NET**, **ASP.NET Core**, **Node.js**, **Python**, y **.NET Core**: usar la herramienta de publicación para implementar en una variable local carpeta. Las opciones disponibles dependen de su tipo de aplicación. En el Explorador de soluciones, haga clic en el proyecto y elija **publicar**y, a continuación, elija **carpeta**. Para obtener más información, consulte [implementar en una carpeta local](quickstart-deploy-to-local-folder.md).

    ![Elija publicar](../deployment/media/quickstart-publish.png)

- **El tiempo de ejecución Visual C++**: puede implementar el tiempo de ejecución de Visual C++ mediante la implementación local o vinculación estática. Para obtener más información, consulte [implementar aplicaciones de escritorio nativas (Visual C++)](/cpp/ide/deploying-native-desktop-applications-visual-cpp.md). 

### <a name="publish-to-web-or-deploy-to-network-share"></a>Publicar en Web o implementar en el recurso compartido de red

- **ASP.NET**, **ASP.NET Core**, **Node.js**, **Python**, y **.NET Core**: puede usar la herramienta de publicación para implementar en un sitio Web mediante FTP o Web Deploy. Para obtener más información, consulte [implementar en un sitio web](quickstart-deploy-to-a-web-site.md).

    En el Explorador de soluciones, haga clic en el proyecto y elija **publicar**. En la herramienta de publicación, seleccione la opción que desee y siga los pasos de configuración.

    ![Elija IIS, FTP, etcetera.](../deployment/media/quickstart-publish-iis-ftp.png)

    También puede implementar aplicaciones ASP.NET y servicios en un número de otras maneras. Para obtener más información, consulte [servicios y aplicaciones web ASP.NET implementar](http://www.asp.net/aspnet/overview/deployment).

- **El tiempo de ejecución Visual C++**: puede implementar el tiempo de ejecución de Visual C++ mediante implementación central. Para obtener más información, consulte [implementar aplicaciones de escritorio nativas (Visual C++)](/cpp/ide/deploying-native-desktop-applications-visual-cpp.md). 

- **Escritorio de Windows** puede publicar una aplicación de escritorio de Windows en un servidor web o un recurso compartido de red mediante la implementación de ClickOnce. A continuación, los usuarios podrán instalar la aplicación con un solo clic. Para obtener más información, consulte [implementar una aplicación de escritorio con ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) y [implementar una aplicación nativa con ClickOnce](/cpp/ide/clickonce-deployment-for-visual-cpp-applications).

### <a name="publish-to-azure"></a>Publicar en Azure

- **ASP.NET, ASP.NET Core, Python, Node.js y .NET Core** aplicaciones web: puede usar la herramienta de publicación para implementar rápidamente aplicaciones de servicio de aplicaciones de Azure o a una máquina Virtual de Azure. En el Explorador de soluciones, haga clic en el proyecto y elija **publicar**. En el cuadro de diálogo Publicar, elija **servicio de aplicaciones de Microsoft Azure** o **máquinas virtuales de Microsoft Azure**y, a continuación, siga los pasos de configuración.

    ![Elija el servicio de aplicaciones de Azure](../deployment/media/quickstart-publish-azure.png "elegir servicio de aplicaciones de Azure")

    Para publicar en una máquina Virtual de Azure, desplazar a la derecha y seleccione **máquinas virtuales de Microsoft Azure**.

    Para obtener una introducción rápida, consulte [Publish to Azure](quickstart-deploy-to-azure.md). Consulte también [publicar una aplicación de ASP.NET Core en Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). Para la implementación con Git, vea [implementación continua de núcleo de ASP.NET en Azure con Git](/aspnet/core/publishing/azure-continuous-deployment).

    > [!NOTE]
    > Si no dispone de una cuenta de Azure, puede [registrarte aquí](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio).

- Otros **servicios de Azure**: vea específico del [servicio de Azure](https://docs.microsoft.com/azure/#pivot=products) documentación para distintas opciones de implementación que pueden ser compatibles con Visual Studio.

### <a name="publish-to-microsoft-store"></a>Publicar en el almacén de Microsoft

Desde Visual Studio, puede crear paquetes de aplicaciones para su implementación en Microsoft Store.

- **UWP**: también puede empaquetar la aplicación e implementarlo con elementos de menú. Para obtener más información, consulte [empaquetar una aplicación UWP con Visual Studio](/windows/uwp/packaging/packaging-uwp-apps).

    ![Crear un paquete de aplicación](../deployment/media/feature-tour-create-app-package.jpg)

- **Escritorio de Windows**: puede implementar a Microsoft Store con el puente de escritorio a partir de Visual Studio 2017 versión 15.4. Para ello, empiece por crear un proyecto de empaquetado de aplicaciones de Windows. Para obtener más información, consulte [empaquetar una aplicación de escritorio de Microsoft Store (escritorio Bridge)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net).

    ![Puente de escritorio](../deployment/media/feature-tour-desktop-bridge.png)

### <a name="create-an-installer-package-windows-client"></a>Crear un paquete del instalador (cliente de Windows)

- Se puede crear un instalador de WiX basadas en MSI utilizando el [WiX conjunto de herramientas de Visual Studio de 2017 extensión](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).

- [InstallShield](https://www.flexerasoftware.com/producer/products/software-installation/installshield-software-installer/tab/requirements) de Flexera Software pueden utilizarse con Visual Studio 2017 (Community Edition no admite). Tenga en cuenta que InstallShield Limited Edition ya no se incluye con Visual Studio y no se admite en Visual Studio de 2017; Póngase en contacto con [Flexera Software](http://learn.flexerasoftware.com/content/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio) sobre disponibilidad futura.

- Si desea crear un proyecto de instalación (vdproj), instale el [extensión de proyectos de instalador de Visual Studio de 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.MicrosoftVisualStudio2017InstallerProjects#overview).

- Puede instalar los componentes necesarios para las aplicaciones de escritorio mediante la configuración de un instalador genérico, que se conoce como un programa previo. Para obtener más información, consulte [requisitos previos de implementación de aplicación](../deployment/application-deployment-prerequisites.md).

### <a name="deploy-to-test-lab"></a>Implementar para el laboratorio de pruebas

Puede habilitar más sofisticadas desarrollo y pruebas mediante la implementación de las aplicaciones en entornos virtuales. Para obtener más información, consulte [pruebas en un entorno de laboratorio](../test/lab-management/using-a-lab-environment-for-your-application-lifecycle.md).

### <a name="devops-deployment"></a>Implementación de DevOps

En un entorno de equipo, puede usar Visual Studio Team Services (VSTS) para habilitar la implementación continua de la aplicación. Para obtener más información, consulte [de compilación y la versión](/vsts/build-release/index) y [implementar en Azure](/vsts/deploy-azure/index).

### <a name="deployment-for-other-app-types"></a>Implementación para otros tipos de aplicación

| Tipo de aplicación | Escenario de implementación | Vínculo |
| --- | --- | --- |
| **Aplicación de Office** | Puede publicar un complemento de Office desde Visual Studio. | [Implementar y publicar el complemento de Office](https://dev.office.com/docs/add-ins/publish/publish) |
| **Servicio WCF o OData**  | Otras aplicaciones pueden utilizar los servicios RIA de WCF que se implementen en un servidor web. | [Desarrollar e implementar WCF Data Services](/dotnet/framework/data/wcf/developing-and-deploying-wcf-data-services) |
| **LightSwitch** | LightSwitch ya no se admite en Visual Studio de 2017, pero todavía se puede implementar desde Visual Studio 2015 y versiones anteriores. | [Implementar aplicaciones de LightSwitch](http://msdn.microsoft.com/Library/4818d933-295c-4ecc-9148-7ad9ca28dcdb) | 

