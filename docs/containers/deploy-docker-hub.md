---
title: Implementación de un contenedor de Docker de ASP.NET Core en Docker Hub | Microsoft Docs
description: Aprenda a usar las herramientas de contenedor de Visual Studio para implementar una aplicación web de ASP.NET Core en Docker Hub.
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: how-to
ms.date: 07/23/2019
ms.author: ghogen
monikerRange: '>=vs-2019'
ms.openlocfilehash: e51088d135d0d2cdcc5d1bcca71f72fed8b73fd2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867664"
---
# <a name="deploy-to-docker-hub"></a>Implementación en Docker Hub

Docker Hub proporciona un servicio de hospedaje práctico para los repositorios de imágenes. Puede implementar fácilmente en Docker Hub de forma manual desde Visual Studio.

## <a name="create-a-docker-account-and-docker-hub-repository"></a>Creación de una cuenta de Docker y un repositorio de Docker Hub

[Regístrese](https://hub.docker.com/signup) para obtener una cuenta de Docker si aún no tiene una.

Si no tiene un repositorio de Docker Hub, cree uno en [Docker Hub](https://hub.docker.com/).

## <a name="publish-the-image-for-a-single-project-to-docker-hub"></a>Publicación de la imagen de un solo proyecto en Docker Hub

1. Haga clic con el botón derecho en el nodo de proyecto y elija **Publicar**. Aparece una pantalla que muestra las opciones de implementación.

   ![Captura de pantalla de las opciones de implementación](media/container-tools/vs-2019/docker-container-registry.png)

1. Elija **Container Registry para Docker**  y luego **Docker Hub**.

   ![Captura de pantalla del cuadro de diálogo Publicar - Elegir Docker Hub](media/deploy-docker-hub/container-tools-docker-hub-deploy.png)

1. Escriba las credenciales de Docker.

   ![Captura de pantalla del cuadro de diálogo Docker Hub](media/deploy-docker-hub/container-tools-docker-hub-credentials.png)

1. Si se conecta a su propio repositorio (que no es parte de una organización), deje activada la casilla **Publicar en un repositorio personal**. Si el repositorio es propiedad de una organización, desactive la casilla y escriba el nombre de la organización. Escriba su nombre de usuario y contraseña de la cuenta de Docker que tenga permisos para acceder al repositorio al que se está conectando y, a continuación, seleccione **Guardar**.

   Visual Studio intenta implementar la imagen en Docker Hub.  Si se realiza correctamente, aparece la pantalla **Publicar** con la dirección URL de la imagen del repositorio, la etiqueta de la imagen, el repositorio y la configuración de compilación (por ejemplo, **Versión**).

   ![Captura de pantalla de la pantalla Publicar](media/deploy-docker-hub/container-tools-docker-hub-finished.png)

1. Para actualizar la imagen en cualquier momento, haga clic en el botón **Publicar** en esta página.  O bien, puede modificar o quitar el perfil mediante los vínculos situados debajo de la dirección URL.

## <a name="next-steps"></a>Pasos siguientes

Publique en [Azure Container Registry](/azure/container-registry/) siguiendo los pasos que se describen en [Implementación en Azure Container Registry](hosting-web-apps-in-docker.md).

Configure la integración y entrega continuas (CI/CD) con [Azure Pipelines](/azure/devops/pipelines/?view=azure-devops&preserve-view=true).

## <a name="see-also"></a>Vea también

[Implementación en Azure App Service](deploy-app-service.md)
[Herramientas de contenedor de Visual Studio](./index.yml).