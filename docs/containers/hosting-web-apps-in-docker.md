---
title: Implementación de contenedor de Docker de ASP.NET en el registro de ACR
description: Aprenda a usar las herramientas de contenedor de Visual Studio para implementar una aplicación web de ASP.NET Core o de ASP.NET en un registro de contenedor.
author: ghogen
manager: jillfra
ms.assetid: e5e81c5e-dd18-4d5a-a24d-a932036e78b9
ms.devlang: dotnet
ms.topic: how-to
ms.technology: vs-azure
ms.date: 03/14/2019
ms.author: ghogen
ms.openlocfilehash: 4626b64f5e733fec049d56dfe53407cc0fe31566
ms.sourcegitcommit: 2c26d6e6f2a5c56ae5102cdded7b02f2d0fd686c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/13/2020
ms.locfileid: "88168711"
---
# <a name="deploy-an-aspnet-container-to-a-container-registry-using-visual-studio"></a>Implementación de un contenedor ASP.NET en un registro de contenedor con Visual Studio

## <a name="overview"></a>Información general

Docker es un motor de contenedor ligero, semejante de alguna manera a una máquina virtual, que puede utilizar para hospedar aplicaciones y servicios.
Este tutorial le guía a través del uso de Visual Studio para publicar su aplicación en contenedores en una instancia de [Azure Container Registry](https://azure.microsoft.com/services/container-registry).

Si no tiene una suscripción a Azure, cree una [cuenta gratuita](https://azure.microsoft.com/free/dotnet/?utm_source=acr-publish-doc&utm_medium=docs&utm_campaign=docs) antes de empezar.

## <a name="prerequisites"></a>Requisitos previos

Para realizar este tutorial:

::: moniker range="vs-2017"
* Instalar la versión más reciente de [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) con la carga de trabajo "Desarrollo de ASP.NET y web"
::: moniker-end
::: moniker range=">=vs-2019"
* Instalar la versión más reciente de [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) con la carga de trabajo "Desarrollo de ASP.NET y web"
::: moniker-end
* Instalar [Docker para Windows](https://docs.docker.com/docker-for-windows/install/)

## <a name="create-an-aspnet-core-web-app"></a>Crear una aplicación web de ASP.NET Core

Los siguientes pasos le guían en el proceso de creación de una aplicación ASP.NET Core básica que se usará en este tutorial. Si ya tiene un proyecto, puede omitir este paso.

::: moniker range="vs-2017"
[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]
::: moniker-end
::: moniker range=">=vs-2019"
[!INCLUDE [create-aspnet5-app](../azure/includes/vs-2019/create-aspnet5-app-2019.md)]
::: moniker-end

::: moniker range="vs-2017"

## <a name="publish-your-container-to-azure-container-registry"></a>Publique el contenedor en Azure Container Registry.

1. Haga clic con el botón derecho en el **Explorador de soluciones** y elija **Publicar**.
2. En el cuadro de diálogo **Destino de publicación**, seleccione **Container Registry**.
3. Elija **New Azure Container Registry** (Nueva instancia de Azure Container Registry) y haga clic en **Publish** (Publicar).
4. Rellene los valores deseados en el **Create a new Azure Container Registry** (Crear una nueva instancia de Azure Container Registry).

    | Parámetro      | Valor sugerido  | Descripción                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Prefijo de DNS** | Nombre único globalmente | Nombre que identifica de forma única el nuevo registro de contenedor. |
    | **Suscripción** | Elija una suscripción | La suscripción de Azure que se va a usar. |
    | **[Grupo de recursos](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Nombre del grupo de recursos en el que se va a crear el registro de contenedor. Elija **Nuevo** para crear un grupo de recursos nuevo.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Estándar | Nivel de servicio del registro de contenedor  |
    | **Ubicación del registro** | Una ubicación cercana a usted | Elija una ubicación en una [región](https://azure.microsoft.com/regions/) cercana a usted o a otros servicios que usarán el registro de contenedor. |

    ![Cuadro de diálogo Crear Azure Container Registry de Visual Studio](media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png)

5. Haga clic en **Crear**
::: moniker-end

::: moniker range=">=vs-2019"
## <a name="publish-your-container-to-azure-container-registry"></a>Publique el contenedor en Azure Container Registry.
1. Haga clic con el botón derecho en el **Explorador de soluciones** y elija **Publicar**.
2. En el cuadro de diálogo **Publicar**, seleccione **Container Registry para Docker**.

   ![Captura de pantalla del cuadro de diálogo Publicar - Elegir Container Registry para Docker](media/container-tools/vs-2019/docker-container-registry.png)

3. Elija **Crear Azure Container Registry**.
 
   ![Captura de pantalla del cuadro de diálogo Publicar - Elegir Crear Azure Container Registry](media/container-tools/vs-2019/select-existing-or-create-new-azure-container-registry.png)

4. Rellene los valores que quiera en la pantalla **Azure Container Registry**.

    | Configuración      | Valor sugerido  | Descripción                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **Prefijo de DNS** | Nombre único globalmente | Nombre que identifica de forma única el nuevo registro de contenedor. |
    | **Suscripción** | Elija una suscripción | La suscripción de Azure que se va a usar. |
    | **[Grupo de recursos](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  Nombre del grupo de recursos en el que se va a crear el registro de contenedor. Elija **Nuevo** para crear un grupo de recursos nuevo.|
    | **[SKU](/azure/container-registry/container-registry-skus)** | Estándar | Nivel de servicio del registro de contenedor  |
    | **Ubicación del registro** | Una ubicación cercana a usted | Elija una ubicación en una [región](https://azure.microsoft.com/regions/) cercana a usted o a otros servicios que usarán el registro de contenedor. |

    ![Cuadro de diálogo Crear Azure Container Registry de Visual Studio](media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog-2019.png)

5. Haga clic en **Crear**.

6. Haga clic en **Finalizar** para completar el proceso.
::: moniker-end

Ahora puede extraer el contenedor del registro a cualquier host capaz de ejecutar imágenes de Docker, por ejemplo [Azure Container Instances](/azure/container-instances/container-instances-tutorial-deploy-app).

## <a name="see-also"></a>Consulte también

[Inicio rápido: Implementación de una instancia de contenedor en Azure mediante la CLI de Azure](/azure/container-instances/container-instances-quickstart)
