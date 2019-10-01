---
title: Implementación de un contenedor de Docker de ASP.NET Core en Docker Hub | Microsoft Docs
description: Aprenda a usar las herramientas de contenedor de Visual Studio para implementar una aplicación web de ASP.NET Core en Docker Hub.
author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: article
ms.date: 07/23/2019
ms.author: ghogen
ms.openlocfilehash: 267e0c1ed1ac3911aad2161f186bf4a482f069b6
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "71126026"
---
# <a name="deploy-to-docker-hub"></a>Implementación en Docker Hub

Docker Hub proporciona un servicio de hospedaje práctico para los repositorios de imágenes. Puede implementar fácilmente en Docker Hub de forma manual desde Visual Studio.

## <a name="create-a-docker-account-and-docker-hub-repository"></a>Creación de una cuenta de Docker y un repositorio de Docker Hub

[Regístrese](https://hub.docker.com/signup) para obtener una cuenta de Docker si aún no tiene una.

Si no tiene un repositorio de Docker Hub, cree uno en [Docker Hub](https://hub.docker.com/).

## <a name="publish-the-image-for-a-single-project-to-docker-hub"></a>Publicación de la imagen de un solo proyecto en Docker Hub

1. Haga clic con el botón derecho en el nodo de proyecto y elija **Publicar**. Aparece una pantalla que muestra las opciones de implementación.

   ![](media/deploy-docker-hub/container-tools-docker-hub-deploy.png)

1. En **Elegir un destino de publicación**, elija **Container Registry** y luego elija **Docker Hub**. Aparece el cuadro de diálogo **Docker Hub**.

   ![](media/deploy-docker-hub/container-tools-docker-hub-credentials.png)

1. Si se conecta a su propio repositorio (que no es parte de una organización), deje activada la casilla **Publicar en un repositorio personal**. Si el repositorio es propiedad de una organización, desactive la casilla y escriba el nombre de la organización. Escriba su nombre de usuario y contraseña de la cuenta de Docker que tenga permisos para acceder al repositorio al que se está conectando y, a continuación, seleccione **Guardar**.  

   Visual Studio intenta implementar la imagen en Docker Hub.  Si se realiza correctamente, aparece la pantalla **Publicar** con la dirección URL de la imagen del repositorio, la etiqueta de la imagen, el repositorio y la configuración de compilación** (por ejemplo, **Versión**).

   ![](media/deploy-docker-hub/container-tools-docker-hub-finished.png)

1. Para actualizar la imagen en cualquier momento, haga clic en el botón **Publicar** en esta página.  O bien, puede modificar o quitar el perfil mediante los vínculos situados debajo de la dirección URL.

## <a name="next-steps"></a>Pasos siguientes

Publique en [Azure Container Registry](/azure/container-registry/) siguiendo los pasos que se describen en [Implementación en Azure Container Registry](vs-azure-tools-docker-hosting-web-apps-in-docker.md).

Configure la integración y entrega continuas (CI/CD) con [Azure Pipelines](/azure/devops/pipelines/?view=azure-devops).

## <a name="see-also"></a>Vea también

[Implementación en Azure App Service](deploy-app-service.md)
[Herramientas de contenedor de Visual Studio](/visualstudio/containers/).