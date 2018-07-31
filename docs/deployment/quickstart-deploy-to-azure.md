---
title: Publicación en Azure App Service
ms.custom: ''
ms.date: 06/22/2018
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
ms.openlocfilehash: a8de7175b33a91c310da4b3d6d9e4c05c40c3522
ms.sourcegitcommit: 4f82c178b1ac585dcf13b515cc2a9cb547d5f949
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/30/2018
ms.locfileid: "39341695"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio"></a>Publicar una aplicación Web en Azure App Service mediante Visual Studio

Puede usar el **publicar** herramienta para publicar aplicaciones ASP.NET, ASP.NET Core, Node.js y .NET Core en Azure App Service o Azure App Service Linux (con contenedores). Para las aplicaciones de Python, siga los pasos de [Python - publicar en Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md).

[!INCLUDE [quickstart-prereqs-azure](includes/quickstart-prereqs-azure.md)]

## <a name="publish-to-azure-app-service"></a>Publicación en Azure App Service

1. En el Explorador de soluciones, haga clic en el proyecto y elija **publicar** (o use el **compilar** > **publicar** elemento de menú).

    ![El comando Publicar en el menú contextual del proyecto en el Explorador de soluciones](../deployment/media/quickstart-publish.png "elija Publicar")

1. Si previamente ha configurado ningún perfil de publicación, el **publicar** aparece el panel, en qué casos, seleccione **crear nuevo perfil**.

1. En el **elegir un destino de publicación** diálogo cuadro, elija **App Service**.

    ![Elija Azure App Service](../deployment/media/quickstart-publish-azure.png "elegir Azure App Service")

1. Seleccione **Publicar**. El **crear App Service** aparece el cuadro de diálogo. Inicie sesión con cuenta de Azure, si es necesario y, a continuación, la configuración predeterminada del servicio de aplicación rellena los campos.

    ![Creación de App Service](../deployment/media/quickstart-publish-settings-app-service.png "crear Azure App Service")

1. Seleccione **Crear**. Visual Studio implementa la aplicación en Azure App Service y se carga la aplicación web en el explorador. Las propiedades del proyecto **publicar** panel muestra la dirección URL del sitio y otros detalles.

    ![Publicar el panel de propiedades que muestra un perfil de resumen](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="clean-up-resources"></a>Limpiar los recursos

En los pasos anteriores, creó recursos de Azure en un grupo de recursos. Si prevé que no necesita estos recursos en el futuro, puede eliminarlos mediante la eliminación del grupo de recursos.
En el menú izquierdo en Azure portal, seleccione **grupos de recursos** y, a continuación, seleccione **myResourceGroup**.
En la página del grupo de recursos, asegúrese de que los recursos enumerados sean los que desea eliminar.
Seleccione **eliminar**, tipo **myResourceGroup** en el cuadro de texto y, a continuación, seleccione **eliminar**.

## <a name="next-steps"></a>Pasos siguientes

En este tutorial, ha aprendido a usar Visual Studio para crear un perfil de publicación para su implementación en Azure. También puede configurar la publicación de una perfil mediante la importación de configuración de publicación desde Azure App Service.

> [!div class="nextstepaction"]
> [Importar una configuración de publicación e implementar en Azure](tutorial-import-publish-settings-azure.md)
