---
title: Publicar en un sitio web
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7ec5ea0b52c5d0708630a30b7d2b80be2275f3a9
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2020
ms.locfileid: "84173709"
---
# <a name="publish-a-web-app-to-a-web-site-using-visual-studio"></a>Publique una aplicación web en un sitio web mediante Visual Studio

Puede usar la herramienta **Publicar** para publicar aplicaciones ASP.NET, ASP.NET Core, .NET Core y Python en una sitio web desde Visual Studio. En Node.js, se admiten los pasos, pero la interfaz de usuario es diferente.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

> [!NOTE]
> Si tiene que publicar una aplicación de escritorio de Windows en un recurso compartido de archivos de red, vea [Implementación de una aplicación de escritorio con ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# o Visual Basic). Para C++ y CLR, vea [Implementación de ClickOnce para aplicaciones de Visual C++](/cpp/windows/clickonce-deployment-for-visual-cpp-applications), o bien, para C y C ++, vea [Implementación de una aplicación de Visual C++ mediante un proyecto de instalación](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="publish-to-a-web-site"></a>Publicar en un sitio web

1. En el Explorador de soluciones, haga clic con el botón derecho en el proyecto y elija **Publicar** (o use el elemento de menú **Compilar** > **Publicar**).

    ![Comando Publicar en el menú contextual del proyecto del Explorador de soluciones](../deployment/media/quickstart-publish.png "Elección de Publicar")

1. Si previamente ha configurado algún perfil de publicación, aparece el panel **Publicar**. Seleccione **Crear nuevo perfil**.

1. En el cuadro de diálogo **Publicar**, elija **Servidor web (IIS)** .

    ![Elección del destino de publicación](../deployment/media/quickstart-publish-iis.png "Elección de IIS, FTP, etc.")

1. Elija **Web Deploy** como método de implementación. Web Deploy simplifica la implementación de aplicaciones web y sitios web en servidores IIS y debe instalarse como una aplicación en el servidor. Use el [Instalador de plataformaweb](https://www.microsoft.com/web/downloads/platform.aspx) para instalarlo.

    ![Elección del método de implementación](../deployment/media/quickstart-publish-iis-web-deploy.png "Elección de IIS, FTP, etc.")

1. Configure las opciones necesarias del método de publicación y seleccione **Finalizar**. 

    ![Detalles de la conexión Web Deploy](../deployment/media/quickstart-publish-iis-web-deploy-connection-details.png)

1. Para publicar, seleccione **Publicar** en la página de resumen. La ventana de salida muestra el progreso y los resultados de la implementación.

## <a name="next-steps"></a>Pasos siguientes

En este inicio rápido, ha aprendido a usar Visual Studio para crear un perfil de publicación. También puede configurar un perfil de publicación si importa la configuración de publicación.

> [!div class="nextstepaction"]
> [Importar una configuración de publicación e implementar en IIS](tutorial-import-publish-settings-iis.md)
