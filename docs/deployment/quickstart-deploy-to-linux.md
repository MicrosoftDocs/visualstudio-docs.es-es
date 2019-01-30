---
title: Publicar en App Service en Linux
ms.date: 07/23/2018
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- azure
ms.openlocfilehash: 3e80f96e1af39747a6dfa9fb9737ec11bb5baf00
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54951942"
---
# <a name="publish-an-aspnet-core-app-to-app-service-on-linux-using-visual-studio"></a>Publicar una aplicación de ASP.NET Core en App Service en Linux con Visual Studio

Puede usar la herramienta **Publicar** para publicar aplicaciones de ASP.NET Core en Azure App Service en Linux.

Implementar en App Service en Linux mediante la herramienta **Publicar** requiere Visual Studio 2017 versión 15.7.

[!INCLUDE [quickstart-prereqs-azure-linux](includes/quickstart-prereqs-azure-linux.md)]

## <a name="publish-to-app-service-on-linux"></a>Publicar en App Service en Linux

1. En el Explorador de soluciones, haga clic con el botón derecho en el proyecto y elija **Publicar** (o use el elemento de menú **Compilar** > **Publicar**).

    ![Comando Publicar en el menú contextual del proyecto del Explorador de soluciones](../deployment/media/quickstart-publish.png "Elección de Publicar")

1. Si previamente ha configurado algún perfil de publicación, aparecerá el panel **Publicar**, en cuyo caso seleccione **Crear nuevo perfil**.

1. En el cuadro de diálogo **Elegir un destino de publicación**, elija **App Service**.

    ![Elección de Azure App Service](../deployment/media/quickstart-publish-linux.png "Elección Azure App Service")

1. Seleccione **Publicar**. Aparecerá el cuadro de diálogo **Crear servicio de aplicaciones**. Inicie sesión con la cuenta de Azure, si fuera necesario; después la configuración predeterminada de App Service rellenará los campos.

    ![Crear servicio de aplicaciones](../deployment/media/quickstart-publish-settings-app-service-linux.png "Crear Azure App Service")

1. Seleccione **Crear**. Visual Studio implementará la aplicación en Azure App Service y la aplicación web se cargará en el explorador. El panel de propiedades del proyecto **Publicar** muestra la dirección URL del sitio y otros detalles.

    ![Panel de propiedades Publicar que muestra un resumen de perfil](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="clean-up-resources"></a>Limpiar los recursos

En los pasos anteriores, ha creado recursos de Azure en un grupo de recursos. Si no prevé necesitar estos recursos en el futuro, puede eliminarlos mediante la eliminación del grupo de recursos.
En el menú izquierdo de Azure Portal, seleccione **Grupos de recursos** y luego **myResourceGroup**.
En la página del grupo de recursos, asegúrese de que los recursos que aparecen son los que quiere eliminar.
Seleccione **Eliminar**, escriba **myResourceGroup** en el cuadro de texto y luego seleccione **Eliminar**.

## <a name="next-steps"></a>Pasos siguientes

En este inicio rápido, ha aprendido a usar Visual Studio para crear un perfil de publicación para su implementación en App Service en Linux. Puede que desee obtener más información sobre la publicación en Linux con Azure.

> [!div class="nextstepaction"]
> [App Service de Linux](/azure/app-service/containers/app-service-linux-intro)
