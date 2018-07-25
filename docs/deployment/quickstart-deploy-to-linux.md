---
title: Publicar en App Service en Linux
ms.custom: ''
ms.date: 07/23/2018
ms.technology: vs-ide-deployment
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- azure
ms.openlocfilehash: e0268c2e65cd08274c2267ad2a4969f6015cbaf4
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2018
ms.locfileid: "39234880"
---
# <a name="publish-an-aspnet-core-app-to-app-service-on-linux-using-visual-studio"></a>Publicar una aplicación ASP.NET Core en App Service en Linux mediante Visual Studio

Puede usar el **publicar** herramienta para publicar aplicaciones de ASP.NET Core en Azure App Service en Linux.

[!INCLUDE [quickstart-prereqs-azure-linux](includes/quickstart-prereqs-azure-linux.md)]

## <a name="publish-to-app-service-on-linux"></a>Publicar en App Service en Linux

1. En el Explorador de soluciones, haga clic en el proyecto y elija **publicar** (o use el **compilar** > **publicar** elemento de menú).

    ![El comando Publicar en el menú contextual del proyecto en el Explorador de soluciones](../deployment/media/quickstart-publish.png "elija Publicar")

1. Si previamente ha configurado ningún perfil de publicación, el **publicar** aparece el panel, en qué casos, seleccione **crear nuevo perfil**.

1. En el **elegir un destino de publicación** diálogo cuadro, elija **App Service Linux**.

    ![Elija Azure App Service](../deployment/media/quickstart-publish-linux.png "elegir Azure App Service")

1. Seleccione **Publicar**. El **crear App Service** aparece el cuadro de diálogo. Inicie sesión con cuenta de Azure, si es necesario y, a continuación, la configuración predeterminada del servicio de aplicación rellena los campos.

    ![Creación de App Service](../deployment/media/quickstart-publish-settings-app-service-linux.png "crear Azure App Service")

1. Seleccione **Crear**. Visual Studio implementa la aplicación en Azure App Service y se carga la aplicación web en el explorador. Las propiedades del proyecto **publicar** panel muestra la dirección URL del sitio y otros detalles.

    ![Publicar el panel de propiedades que muestra un perfil de resumen](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="next-steps"></a>Pasos siguientes

En este tutorial, ha aprendido a usar Visual Studio para crear un perfil de publicación para su implementación en App Service en Linux. Puede obtener más información sobre la publicación en Linux con Azure.

> [!div class="nextstepaction"]
> [App Service de Linux](/azure/app-service/containers/app-service-linux-intro)
