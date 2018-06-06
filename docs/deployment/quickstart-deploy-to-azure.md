---
title: Publicar en servicio de aplicación de Azure - Visual Studio | Documentos de Microsoft
ms.custom: ''
ms.date: 11/22/2017
ms.technology: vs-ide-deployment
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- azure
ms.openlocfilehash: f91fd6e8c101b674b745c120978a47adb17c9b91
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2018
ms.locfileid: "34765380"
---
# <a name="publish-an-aspnet-or-aspnet-core-app-to-azure-app-service-using-visual-studio"></a>Publicar una aplicación ASP.NET o ASP.NET Core para el servicio de aplicaciones de Azure con Visual Studio

Puede usar el **publicar** herramienta para publicar aplicaciones ASP.NET, ASP.NET Core, Python, Node.js y .NET Core para el servicio de aplicaciones de Azure.

Si no dispone de una cuenta de Azure, puede [registrarte aquí](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio).

## <a name="prerequisites"></a>Requisitos previos

* Debe tener instalado de Visual Studio 2017 y **ASP.NET y desarrollo web** carga de trabajo y. **Desarrollo de escritorio NET** carga de trabajo. Para una aplicación .NET Core, necesitará el. **NET Core** carga de trabajo.

    Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) para instalarlo de forma gratuita.

## <a name="create-a-new-project"></a>Crear un proyecto nuevo 

1. En Visual Studio, seleccione **Archivo > Nuevo proyecto**.

1. En **Visual C#** o **Visual Basic**, elija **Web**y, a continuación, en el panel central elija **aplicación Web de ASP.NET (.NET Framework)**(solo C#) o **aplicación Web de ASP.NET Core**y, a continuación, haga clic en **Aceptar**.

1. Elija **MVC** (o elija **aplicación Web (Model-View-Controller)** para .NET Core), asegúrese de que **sin autenticación** está seleccionada y, a continuación, haga clic en **Aceptar** .

1. Escriba un nombre como **MyWebApp** y haga clic en **Aceptar**.

    Visual Studio crea el proyecto.

1. Elija **generar > compilar solución** para compilar el proyecto.

## <a name="publish-to-azure-app-service"></a>Publicación en Azure App Service

1. En el Explorador de soluciones, haga clic con el botón derecho en el proyecto y seleccione **Publicar**.

    ![Elija publicar](../deployment/media/quickstart-publish-aspnet.png "elija Publicar")

1. Si previamente ha configurado ningún perfil de publicación, la **publicar** aparece el panel. Haga clic en **crear nuevo perfil**.

1. En el **elegir un destino de publicación** diálogo cuadro, elija **servicio de aplicaciones**.

    ![Elija el servicio de aplicaciones de Azure](../deployment/media/quickstart-publish-azure.png "elegir servicio de aplicaciones de Azure")

1. Haga clic en **Publicar**.

    El **crear servicio en la aplicación** aparece el cuadro de diálogo.

    ![Crear servicio de aplicaciones](../deployment/media/quickstart-publish-settings-app-service.png "crear servicio de aplicaciones de Azure")
    
1. Si no se ha conectado en Visual Studio, inicie sesión y, a continuación, la configuración predeterminada del servicio de aplicación rellena los campos.

    El perfil de configuración que se abre el cuadro de diálogo de publicación.

    ![Elija la carpeta](../deployment/media/quickstart-publish-settings-web.png "Seleccionar carpeta")

    En este cuadro de diálogo, puede seleccionar la suscripción que estás usando, seleccione o cree un grupo de recursos de Azure, etcetera.

1. Haga clic en **Crear**.

    Visual Studio implementa la aplicación en el servicio de aplicaciones de Azure y la aplicación web se carga en el explorador.

    En el resumen de la **publicar** panel, consulte la dirección URL del sitio para el nuevo servicio de aplicación de Azure.

## <a name="next-steps"></a>Pasos siguientes

En este tutorial, aprendió a utilizar Visual Studio para crear un perfil de publicación para su implementación en Azure. También puede configurar una publicación de perfil mediante la importación de publicar la configuración de servicio de aplicaciones de Azure.

> [!div class="nextstepaction"]
> [Importar una configuración de publicación e implementar en Azure](tutorial-import-publish-settings-azure.md)
