---
title: Publicación en Azure App Service
description: Obtenga información sobre los métodos para publicar aplicaciones ASP.NET, ASP.NET Core, Node.js y .NET Core en Azure App Service o Azure App Service para Linux.
ms.custom: SEO-VS-2020
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- azure
ms.openlocfilehash: 11e655adcfecb9ab63479275b64873fa4c9e6d0f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927449"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio"></a>Publique una aplicación web en Azure App Service mediante Visual Studio

Para las aplicaciones ASP.NET, ASP.NET Core, Node.js y .NET Core, publique en Azure App Service o Azure App Service para Linux (con contenedores) mediante uno de los métodos siguientes.

* Para la implementación continua (o automática) de aplicaciones, use Azure DevOps con [Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops&preserve-view=true).

* Para la implementación de un solo uso (o manual) de aplicaciones, use la herramienta de **publicación** de Visual Studio para implementar aplicaciones ASP.NET, ASP.NET Core, Node.js y .NET Core en Azure App Service o [App Service para Linux](../deployment/quickstart-deploy-to-linux.md) (con contenedores). En el caso de las aplicaciones de Python, siga los pasos de [Publicación en Azure App Service (Python)](../python/publishing-python-web-applications-to-azure-from-visual-studio.md).

En este artículo se describe cómo usar la herramienta de **publicación** para la implementación de un solo uso.

[!INCLUDE [quickstart-prereqs-azure](includes/quickstart-prereqs-azure.md)]

## <a name="publish-to-azure-app-service-on-windows"></a>Publicación en Azure App Service en Windows

1. En el Explorador de soluciones, haga clic con el botón derecho en el nodo del proyecto y elija **Publicar** (o use el elemento de menú **Compilar** > **Publicar**).

    ![Comando Publicar en el menú contextual del proyecto del Explorador de soluciones](../deployment/media/quickstart-publish.png "Elección de Publicar")

1. Si previamente ha configurado algún perfil de publicación, aparece la ventana **Publicar**. Seleccione **Nuevo**.

1. En la ventana **Publicar**, seleccione **Azure**.

    ![Elección del destino de publicación](../deployment/media/quickstart-publish-azure-new.png)

1. Seleccione **Azure App Service (Windows)** y **Siguiente**.

    ![Elección de Azure App Service en Linux](../deployment/media/quickstart-publish-windows-select-azure-service.png)

1. Si es necesario, inicie sesión con la cuenta de Azure. Seleccione **Create a new Azure App Service...** (Crear una instancia de Azure App Service)

    ![Vínculo para crear una instancia de Azure App Service](../deployment/media/quickstart-publish-windows-create-new-link.png)

1. En el cuadro de diálogo **Create Azure App Service (Windows)** (Crear Azure App Service [Windows]), se rellenan los campos de entrada **Nombre de la aplicación,** , **Grupo de recursos** y **Plan de App Service**. Puede mantener estos nombres o cambiarlos. Cuando esté preparado, seleccione **Guardar**.

    ![Captura de pantalla del cuadro de diálogo Create Azure App Service (Windows) (Crear Azure App Service [Windows]) con los campos Nombre, Suscripción, Grupo de recursos y Plan de hospedaje rellenados.](../deployment/media/quickstart-publish-windows-create-new-dialog.png)

1. En el cuadro de diálogo **Publicar**, la instancia recién creada se ha seleccionado automáticamente. Cuando esté listo, seleccione **Finalizar**.

    ![Captura de pantalla de la ventana Publicar, a la que se accede desde el Explorador de soluciones de Visual Studio. Azure está seleccionado como destino de publicación.](../deployment/media/quickstart-publish-windows-select-instance.png)

1. Seleccione **Publicar**. Visual Studio implementará la aplicación en Azure App Service y la aplicación web se cargará en el explorador. El panel de propiedades del proyecto **Publicar** muestra la dirección URL del sitio y otros detalles.

    ![Panel de propiedades Publicar que muestra un resumen de perfil](../deployment/media/quickstart-publish-windows-summary-page.png)

## <a name="clean-up-resources"></a>Limpiar los recursos

En los pasos anteriores, creó recursos de Azure en un grupo de recursos. Si no prevé necesitar estos recursos en el futuro, puede eliminarlos mediante la eliminación del grupo de recursos.
En el menú izquierdo de Azure Portal, seleccione **Grupos de recursos** y luego **myResourceGroup**.
En la página del grupo de recursos, asegúrese de que los recursos que aparecen son los que quiere eliminar.
Seleccione **Eliminar**, escriba **myResourceGroup** en el cuadro de texto y luego seleccione **Eliminar**.

## <a name="next-steps"></a>Pasos siguientes

En este inicio rápido, ha aprendido a usar Visual Studio para crear un perfil de publicación para su implementación en Azure. También puede configurar un perfil de publicación si importa la configuración de publicación desde Azure App Service.

> [!div class="nextstepaction"]
> [Importar una configuración de publicación e implementar en Azure](tutorial-import-publish-settings-azure.md)
