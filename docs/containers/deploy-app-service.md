---
title: Implementación de un contenedor de Docker de ASP.NET Core en Azure App Service | Microsoft Docs
description: Aprenda a usar las herramientas de contenedor de Visual Studio para implementar una aplicación web de ASP.NET Core en Azure App Service
author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: article
ms.date: 01/27/2020
ms.author: ghogen
ms.openlocfilehash: 6c1d56f788294826853ad441313597255308bb39
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "77027286"
---
# <a name="deploy-an-aspnet-core-container-to-azure-app-service-using-visual-studio"></a>Implementación de un contenedor de ASP.NET Core en Azure App Service mediante Visual Studio

Este tutorial guía a lo largo del proceso de uso de Visual Studio para publicar la aplicación web en contenedores de ASP.NET Core en [Azure App Service](/azure/app-service). Azure App Service es un servicio adecuado para una aplicación web de un solo contenedor hospedada en Azure.

Si no tiene una suscripción a Azure, cree una [cuenta gratuita](https://azure.microsoft.com/free/dotnet/?utm_source=acr-publish-doc&utm_medium=docs&utm_campaign=docs) antes de empezar.

## <a name="prerequisites"></a>Requisitos previos

Para realizar este tutorial:

::: moniker range="vs-2017"
- Instalar la versión más reciente de [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) con la carga de trabajo "ASP.NET y desarrollo web"
::: moniker-end
::: moniker range=">=vs-2019"
- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) con la carga de trabajo *ASP.NET y desarrollo web*.
::: moniker-end
- Instalar [Docker Desktop](https://docs.docker.com/docker-for-windows/install/)

## <a name="create-an-aspnet-core-web-app"></a>Crear una aplicación web de ASP.NET Core

Los siguientes pasos le guían en el proceso de creación de una aplicación ASP.NET Core básica que se usará en este tutorial.

::: moniker range="vs-2017"
1. En el menú de Visual Studio, seleccione **Archivo > Nuevo > Proyecto**.
2. En la sección **Plantillas** del cuadro de diálogo **Nuevo proyecto**, seleccione **Visual C# > Web**.
3. Seleccione **Aplicación web de ASP.NET Core**.
4. Asigne un nombre a la nueva aplicación (o utilice el predeterminado) y seleccione **Aceptar**.
5. Seleccione **Aplicación web**.
6. Marque la casilla **Enable Docker Support** (Habilitar compatibilidad con Docker).
7. Seleccione el tipo de contenedor **Linux** y haga clic en **Aceptar**. Los contenedores de Windows no se admiten para implementar en Azure App Service como contenedor.
::: moniker-end
::: moniker range=">= vs-2019"
1. En la ventana de inicio de Visual Studio, seleccione **Crear un nuevo proyecto**.
1. Seleccione **Aplicación web ASP.NET Core** y luego **Siguiente**.
1. Asigne un nombre a la nueva aplicación (o use el predeterminado) y seleccione **Crear**.
1. Seleccione **Aplicación web**.
1. Decida si quiere o no compatibilidad de SSL mediante la casilla **Configure for HTTPS** (Configurar para HTTPS).
1. Marque la casilla **Enable Docker Support** (Habilitar compatibilidad con Docker).
1. Seleccione el tipo de contenedor y haga clic en **Crear**. Los contenedores de Windows no se admiten para implementar en Azure App Service como contenedor.
::: moniker-end

## <a name="deploy-the-container-to-azure"></a>Implementación del contenedor en Azure

1. Haga clic con el botón derecho en el **Explorador de soluciones** y elija **Publicar**.
1. En el cuadro de diálogo de destino de publicación, seleccione **App Service Linux** o **App Service**. Este es el sistema operativo que hospedará el servidor web.
1. Puede publicar solo en App Service o en App Service y Azure Container Registry (ACR). Para publicar el contenedor en Azure Container Registry (ACR), seleccione **Create new App Service for containers** (Crear App Service para contenedores) y haga clic en **Publicar**.

   ![Captura de pantalla del cuadro de diálogo de publicación](media/deploy-app-service/publish-app-service-linux.PNG)

   Para publicar solo en Azure App Service sin usar Azure Container Registry, seleccione **Crear nuevo** y haga clic en **Publicar**.

1. Compruebe que ha iniciado sesión con la cuenta asociada a la suscripción de Azure y seleccione un nombre único, una suscripción, un grupo de recursos, un plan de hospedaje y un registro de contenedor (si procede) o acepte los valores predeterminados.

   ![Captura de pantalla de la configuración de publicación](media/deploy-app-service/publish-app-service-linux2.png)

1. Seleccione **Create**. El contenedor se implementa en Azure en el grupo de recursos y el registro de contenedor seleccionados. Este proceso tarda un poco. Cuando haya finalizado, la pestaña **Publicar** muestra información sobre lo que se ha publicado, incluida la dirección URL del sitio.

   ![Captura de pantalla de la pestaña de publicación](media/deploy-app-service/publish-succeeded.PNG)

1. Haga clic en el vínculo del sitio para comprobar que la aplicación funciona según lo previsto en Azure.

   ![Captura de pantalla de la aplicación web](media/deploy-app-service/web-application-running.png)

1. El perfil de publicación se guarda con todos los detalles seleccionados, como el grupo de recursos y el registro de contenedor.

1. Para volver a implementar con el mismo perfil de publicación, use el botón **Publicar**, el botón **Publicar** de la ventana **Actividad de publicación web** o haga clic con el botón derecho en el proyecto en el **Explorador de soluciones** y seleccione el elemento **Publicar** en el menú contextual.

## <a name="view-container-settings"></a>Visualización de la configuración del contenedor

En [Azure Portal](https://portal.azure.com), puede abrir la instancia de App Service implementada.

Para ver la configuración de la instancia implementada de App Service, abra el menú **Configuración del contenedor* (si usa Visual Studio 2019, versión 16.4 o posterior).

![Captura de pantalla del menú Configuración del contenedor en Azure Portal](media/deploy-app-service/container-settings-menu.png)

Desde allí, puede ver la información del contenedor, ver o descargar registros, o bien configurar la implementación continua. Vea [CI/CD continua en Azure App Service](/azure/app-service/containers/app-service-linux-ci-cd).

## <a name="clean-up-resources"></a>Limpiar los recursos

Para quitar todos los recursos de Azure asociados a este tutorial, elimine el grupo de recursos mediante [Azure Portal](https://portal.azure.com). Para buscar el grupo de recursos asociado a una aplicación web publicada, seleccione **Ver** > **Otras ventanas** > **Actividad de publicación web** y luego el icono de engranaje. Se abre la pestaña **Publicar**, que contiene el grupo de recursos.

En Azure Portal, seleccione **Grupos de recursos** y luego el grupo de recursos para abrir su página de detalles. Compruebe que se trata del grupo de recursos correcto, seleccione **Quitar grupo de recursos**, escriba el nombre y seleccione **Eliminar**.

## <a name="next-steps"></a>Pasos siguientes

Obtenga más información sobre [Azure App Service Linux](/azure/app-service/containers/app-service-linux-intro).

## <a name="see-also"></a>Vea también

[Implementación en Azure Container Registry](hosting-web-apps-in-docker.md)