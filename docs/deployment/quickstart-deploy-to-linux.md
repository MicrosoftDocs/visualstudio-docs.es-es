---
title: Publicar en App Service en Linux
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- azure
ms.openlocfilehash: 1e05862aa57c24bfa8f17d551762054278dd6e52
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/20/2020
ms.locfileid: "72806864"
---
# <a name="publish-an-aspnet-core-app-to-app-service-on-linux-using-visual-studio"></a>Publicar una aplicación de ASP.NET Core en App Service en Linux con Visual Studio

A partir de Visual Studio 2017 versión 15.7, puede publicar aplicaciones ASP.NET Core en Azure App Service Linux (con contenedores) mediante uno de los métodos siguientes.

* Para la implementación continua (o automática) de aplicaciones, use Azure DevOps con [Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops).

* Para la implementación de un solo uso (o manual) de aplicaciones, use la herramienta de **publicación** de Visual Studio para publicar aplicaciones ASP.NET Core en App Service para Linux (con contenedores).

En este artículo se describe cómo usar la herramienta de **publicación** para la implementación de un solo uso.

[!INCLUDE [quickstart-prereqs-azure-linux](includes/quickstart-prereqs-azure-linux.md)]

## <a name="publish-to-app-service-on-linux"></a>Publicar en App Service en Linux

1. En el Explorador de soluciones, haga clic con el botón derecho en el proyecto y elija **Publicar** (o use el elemento de menú **Compilar** > **Publicar**).

    ![Comando Publicar en el menú contextual del proyecto del Explorador de soluciones](../deployment/media/quickstart-publish.png "Elección de Publicar")

1. Si previamente ha configurado algún perfil de publicación, aparece el panel **Publicar**, en cuyo caso seleccione **Crear nuevo perfil**.

1. En el cuadro de diálogo **Elegir un destino de publicación**, elija **App Service**.

    ![Elegir Azure App Service](../deployment/media/quickstart-publish-linux.png "Elegir Azure App Service")

1. Seleccione **Publicar**. Aparecerá el cuadro de diálogo **Crear servicio de aplicaciones**. Inicie sesión con la cuenta de Azure, si fuera necesario; después la configuración predeterminada de App Service rellenará los campos.

    ![Crear servicio de aplicaciones](../deployment/media/quickstart-publish-settings-app-service-linux.png "Crear una instancia de Azure App Service")

1. Seleccione **Crear**. Visual Studio implementará la aplicación en Azure App Service y la aplicación web se cargará en el explorador. El panel de propiedades del proyecto **Publicar** muestra la dirección URL del sitio y otros detalles.

    ![Panel de propiedades Publicar que muestra un resumen de perfil](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="clean-up-resources"></a>Limpieza de recursos

En los pasos anteriores, creó recursos de Azure en un grupo de recursos. Si no cree que vaya a necesitar estos recursos en el futuro, puede eliminarlos mediante la eliminación del grupo de recursos.
En el menú izquierdo de Azure Portal, haga clic en **Grupos de recursos** y en **myResourceGroup**.
En la página del grupo de recursos, asegúrese de que los recursos enumerados sean los que desea eliminar.
Seleccione **Eliminar**, escriba **myResourceGroup** en el cuadro de texto y seleccione **Eliminar**.

## <a name="next-steps"></a>Pasos siguientes

En este inicio rápido, ha aprendido a usar Visual Studio para crear un perfil de publicación para su implementación en App Service en Linux. Puede que desee obtener más información sobre la publicación en Linux con Azure.

> [!div class="nextstepaction"]
> [App Service de Linux](/azure/app-service/containers/app-service-linux-intro)
