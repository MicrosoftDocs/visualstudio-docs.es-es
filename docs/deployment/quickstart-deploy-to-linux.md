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
ms.openlocfilehash: 8130608f7f94efa279775f532e0022df2f2a7f1a
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2020
ms.locfileid: "90037678"
---
# <a name="publish-an-aspnet-core-app-to-app-service-on-linux-using-visual-studio"></a>Publicar una aplicación de ASP.NET Core en App Service en Linux con Visual Studio

A partir de Visual Studio 2017 versión 15.7, puede publicar aplicaciones ASP.NET Core en Azure App Service Linux (con contenedores) mediante uno de los métodos siguientes.

* Para la implementación continua (o automática) de aplicaciones, use Azure DevOps con [Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops).

* Para la implementación de un solo uso (o manual) de aplicaciones, use la herramienta de **publicación** de Visual Studio para publicar aplicaciones ASP.NET Core en App Service para Linux (con contenedores).

En este artículo se describe cómo usar la herramienta de **publicación** para la implementación de un solo uso.

[!INCLUDE [quickstart-prereqs-azure-linux](includes/quickstart-prereqs-azure-linux.md)]

## <a name="publish-to-azure-app-service-on-linux"></a>Publicación en Azure App Service en Linux

1. En el Explorador de soluciones, haga clic con el botón derecho en el proyecto y elija **Publicar** (o use el elemento de menú **Compilar** > **Publicar**).

    ![Comando Publicar en el menú contextual del proyecto del Explorador de soluciones](../deployment/media/quickstart-publish.png "Elección de Publicar")

1. Si previamente ha configurado algún perfil de publicación, aparece la ventana **Publicar**. Seleccione **Nuevo**.

1. En la ventana **Publicar**, seleccione **Azure**.

    ![Elección del destino de publicación](../deployment/media/quickstart-publish-azure-new.png)

1. Seleccione **Azure App Service (Linux)** y **Siguiente**.

    ![Elección de Azure App Service en Linux](../deployment/media/quickstart-publish-linux-select-azure-service.png)

1. Si es necesario, inicie sesión con la cuenta de Azure. Seleccione **Create a new Azure App Service...** (Crear una instancia de Azure App Service)

    ![Vínculo para crear una instancia de Azure App Service](../deployment/media/quickstart-publish-linux-create-new-link.png)

1. En el cuadro de diálogo **Create Azure App Service (Linux)** (Crear Azure App Service [Linux]), se rellenan los campos de entrada **Nombre de la aplicación,** , **Grupo de recursos** y **Plan de App Service**. Puede mantener estos nombres o cambiarlos. Cuando esté preparado, seleccione **Guardar**.

    ![Elegir Azure App Service](../deployment/media/quickstart-publish-linux-create-new-dialog.png)

1. En el cuadro de diálogo **Publicar**, la instancia recién creada se ha seleccionado automáticamente. Cuando esté listo, haga clic en **Finalizar**.

    ![Elegir Azure App Service](../deployment/media/quickstart-publish-linux-select-instance.png)

1. Seleccione **Publicar**. Visual Studio implementará la aplicación en Azure App Service y la aplicación web se cargará en el explorador. El panel de propiedades del proyecto **Publicar** muestra la dirección URL del sitio y otros detalles.

    ![Panel de propiedades Publicar que muestra un resumen de perfil](../deployment/media/quickstart-publish-linux-summary-page.png)

## <a name="clean-up-resources"></a>Limpiar los recursos

En los pasos anteriores, creó recursos de Azure en un grupo de recursos. Si no prevé necesitar estos recursos en el futuro, puede eliminarlos mediante la eliminación del grupo de recursos.
En el menú izquierdo de Azure Portal, seleccione **Grupos de recursos** y luego **myResourceGroup**.
En la página del grupo de recursos, asegúrese de que los recursos que aparecen son los que quiere eliminar.
Seleccione **Eliminar**, escriba **myResourceGroup** en el cuadro de texto y luego seleccione **Eliminar**.

## <a name="next-steps"></a>Pasos siguientes

En este inicio rápido, ha aprendido a usar Visual Studio para crear un perfil de publicación para su implementación en App Service en Linux. Puede que desee obtener más información sobre la publicación en Linux con Azure.

> [!div class="nextstepaction"]
> [App Service de Linux](/azure/app-service/containers/app-service-linux-intro)