---
title: Publicación en Azure App Service
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- azure
ms.openlocfilehash: 114c6aca7ec7ed05858868b22f7547b0a071420f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62927738"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio"></a>Publique una aplicación web en Azure App Service mediante Visual Studio

Para las aplicaciones ASP.NET, ASP.NET Core, Node.js y .NET Core, publique en Azure App Service o Azure App Service para Linux (con contenedores) mediante uno de los métodos siguientes.

* Para la implementación continua (o automática) de aplicaciones, use Azure DevOps con [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/get-started-yaml?view=azdevops).

* Para la implementación de un solo uso (o manual) de aplicaciones, use la herramienta de **publicación** de Visual Studio para implementar aplicaciones ASP.NET, ASP.NET Core, Node.js y .NET Core en Azure App Service o App Service para Linux (con contenedores). En el caso de las aplicaciones de Python, siga los pasos de [Publicación en Azure App Service (Python)](../python/publishing-python-web-applications-to-azure-from-visual-studio.md).

En este artículo se describe cómo usar la herramienta de **publicación** para la implementación de un solo uso.

[!INCLUDE [quickstart-prereqs-azure](includes/quickstart-prereqs-azure.md)]

## <a name="publish-to-azure-app-service"></a>Publicación en Azure App Service

1. En el Explorador de soluciones, haga clic con el botón derecho en el proyecto y elija **Publicar** (o use el elemento de menú **Compilar** > **Publicar**).

    ![Comando Publicar en el menú contextual del proyecto del Explorador de soluciones](../deployment/media/quickstart-publish.png "Elección de Publicar")

1. Si previamente ha configurado algún perfil de publicación, aparece el panel **Publicar**, en cuyo caso seleccione **Crear nuevo perfil**.

1. En el cuadro de diálogo **Elegir un destino de publicación**, elija **App Service**.

    ![Elección de Azure App Service](../deployment/media/quickstart-publish-azure.png "Elección Azure App Service")

1. Seleccione **Publicar**. Aparecerá el cuadro de diálogo **Crear servicio de aplicaciones**. Inicie sesión con la cuenta de Azure, si fuera necesario; después la configuración predeterminada de App Service rellenará los campos.

    ![Crear servicio de aplicaciones](../deployment/media/quickstart-publish-settings-app-service.png "Crear Azure App Service")

1. Seleccione **Crear**. Visual Studio implementará la aplicación en Azure App Service y la aplicación web se cargará en el explorador. El panel de propiedades del proyecto **Publicar** muestra la dirección URL del sitio y otros detalles.

    ![Panel de propiedades Publicar que muestra un resumen de perfil](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="clean-up-resources"></a>Limpiar los recursos

En los pasos anteriores, ha creado recursos de Azure en un grupo de recursos. Si no prevé necesitar estos recursos en el futuro, puede eliminarlos mediante la eliminación del grupo de recursos.
En el menú izquierdo de Azure Portal, seleccione **Grupos de recursos** y luego **myResourceGroup**.
En la página del grupo de recursos, asegúrese de que los recursos que aparecen son los que quiere eliminar.
Seleccione **Eliminar**, escriba **myResourceGroup** en el cuadro de texto y luego seleccione **Eliminar**.

## <a name="next-steps"></a>Pasos siguientes

En este inicio rápido, ha aprendido a usar Visual Studio para crear un perfil de publicación para su implementación en Azure. También puede configurar un perfil de publicación si importa la configuración de publicación desde Azure App Service.

> [!div class="nextstepaction"]
> [Importar una configuración de publicación e implementar en Azure](tutorial-import-publish-settings-azure.md)
