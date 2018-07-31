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
ms.openlocfilehash: aa4afce6ef50284f1f966054e805b55c86f4daaf
ms.sourcegitcommit: 4f82c178b1ac585dcf13b515cc2a9cb547d5f949
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/30/2018
ms.locfileid: "39341753"
---
# <a name="publish-an-aspnet-core-app-to-app-service-on-linux-using-visual-studio"></a>Publicar una aplicación ASP.NET Core en App Service en Linux mediante Visual Studio

Puede usar el **publicar** herramienta para publicar aplicaciones de ASP.NET Core en Azure App Service en Linux.

Implementación en App Service en Linux mediante el **publicar** herramienta requiere Visual Studio 2017 versión 15.7.

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

## <a name="clean-up-resources"></a>Limpiar los recursos

En los pasos anteriores, creó recursos de Azure en un grupo de recursos. Si prevé que no necesita estos recursos en el futuro, puede eliminarlos mediante la eliminación del grupo de recursos.
En el menú izquierdo en Azure portal, seleccione **grupos de recursos** y, a continuación, seleccione **myResourceGroup**.
En la página del grupo de recursos, asegúrese de que los recursos enumerados sean los que desea eliminar.
Seleccione **eliminar**, tipo **myResourceGroup** en el cuadro de texto y, a continuación, seleccione **eliminar**.

## <a name="next-steps"></a>Pasos siguientes

En este tutorial, ha aprendido a usar Visual Studio para crear un perfil de publicación para su implementación en App Service en Linux. Puede obtener más información sobre la publicación en Linux con Azure.

> [!div class="nextstepaction"]
> [App Service de Linux](/azure/app-service/containers/app-service-linux-intro)
