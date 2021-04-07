---
title: Publicación en Azure App Service
description: Puede usar la herramienta Publicar para publicar aplicaciones ASP.NET Core en Azure App Service.
ms.date: 01/17/2019
helpviewer_keywords:
- deployment, website
ms.assetid: 8524a4c5-97a9-41ac-a2a0-034efb9bfc57
author: sayedihashimi
ms.author: sayedha
manager: unniravindranathan
ms.prod: visual-studio-mac
ms.custom: video
ms.topic: how-to
ms.workload:
- azure
ms.openlocfilehash: e0fdabe38f2696540db1a3b629609dbc1c42d821
ms.sourcegitcommit: 155d5f0fd54ac1d20df2f5b0245365924faa3565
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/31/2021
ms.locfileid: "106083634"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio-for-mac"></a>Publicación de una aplicación web en Azure App Service mediante Visual Studio para Mac

Puede usar la herramienta Publicar para publicar aplicaciones ASP.NET Core en Azure App Service.

## <a name="prerequisites"></a>Requisitos previos

- [Visual Studio 2017 para Mac](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs4mac2017) instalado con ASP.NET Core habilitado.
- Una suscripción de Azure. Si aún no tiene suscripción, puede [registrarse gratis](https://azure.microsoft.com/free/dotnet/), lo que incluye 200 USD de crédito durante 30 días y 12 meses de servicios populares gratis.
- Un proyecto de ASP.NET Core. Si aún no tiene un proyecto, puede [crear uno nuevo](./create-new-projects.md?view=vsmac-2017&preserve-view=true).

## <a name="publish-to-azure-app-service"></a>Publicación en Azure App Service

 1. En el Panel de solución, haga clic con el botón derecho en el proyecto y elija **Publicar**.

    ![Menú contextual Publicar](media/publish-context-menu.png)

 2. Si ya había publicado este proyecto en Azure App Service, verá el perfil de publicación en el menú. Seleccione ese perfil de publicación para iniciar el proceso de publicación.

 3. Para publicar este proyecto en Azure App Service por primera vez, seleccione **Publicar en Azure App Service**

    ![Menú contextual Publicar en Azure App Service](media/publish-to-azure-context-menu.png)

 4. Aparece el cuadro de diálogo **Publicar en Azure App Service**, donde se muestran los App Service existentes. Para publicar en un App Service existente, seleccione el App Service en la lista y, luego, haga clic en **Publicar**.

    ![Cuadro de diálogo Publicar en Azure App Service](media/publish-to-app-service-dialog.png)

 5. Para crear un nuevo App Service, haga clic en el botón **Nuevo**.

    ![Cuadro de diálogo Publicar en Azure App Service](media/publish-to-app-service-dialog-new-selected.png)

 6. Aparece el cuadro de diálogo **Nuevo App Service**. En este cuadro de diálogo puede configurar las opciones del nuevo App Service.

    ![Cuadro de diálogo Nuevo App Service](media/publish-new-app-service.png)

    Aquí hay algunas opciones que puede personalizar. El nombre predeterminado del App Service es el nombre de proyecto. Si el nombre no está disponible, se muestra una señal de advertencia en el lado derecho del campo de entrada. El nombre del App Service se usará en la dirección URL del sitio web, por lo que el nombre debe ser válido para usarlo en una URL.

    Puede cambiar la suscripción a la que se asociará el App Service mediante la lista desplegable **Suscripción**.

    Puede seleccionar un **Grupo de recursos** existente mediante la lista desplegable o puede crear uno nuevo con el botón **+** .

    Para el plan de App Service, seleccione uno existente o cree uno nuevo mediante el botón de radio **Personalizado**.

    Para crear su nuevo App Service y publicar el proyecto en él, haga clic en **Crear**.

    Tras hacer clic en **Crear**, se descartará el cuadro de diálogo **Nuevo App Service** y verá el siguiente mensaje que indica que ha iniciado la creación del App Service.

      ![Mensaje Crear App Service](media/publish-create-app-service-message.png)

    Al hacer clic **Aceptar**, se descarta el mensaje y puede continuar trabajando en el proyecto. Puede ver el estado del proceso de publicación con la barra de estado en la parte superior del IDE. Una vez que la aplicación web se ha publicado correctamente, se abre el sitio con el explorador predeterminado.

## <a name="related-video"></a>Vídeo relacionado

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Publish-to-Azure/player]