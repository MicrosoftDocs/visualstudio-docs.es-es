---
title: Publicar la aplicación en una carpeta
description: Procedimiento para publicar una aplicación web en una carpeta con Visual Studio para Mac.
ms.date: 11/09/2020
helpviewer_keywords:
- deployment, website, console, publish
ms.assetid: e963fb4b-6d32-4d45-86bb-ef7e4d3028b0
author: sayedihashimi
ms.author: sayedha
manager: unniravindranathan
ms.prod: visual-studio-mac
ms.topic: how-to
ms.openlocfilehash: 640cdf8b9c31bad42f8c5664f3cef44c558e2a3a
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493418"
---
# <a name="publish-to-a-folder-using-visual-studio-for-mac"></a>Publicar en una carpeta con Visual Studio para Mac

Puede usar la herramienta Publicar para publicar aplicaciones de consola de .NET Core o ASP.NET Core en una carpeta.

## <a name="prerequisites"></a>Requisitos previos

- [Visual Studio 2019 para Mac](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs4mac2019) instalado con .NET Core habilitado.
- Un proyecto de consola de .NET Core o ASP.NET Core. Si aún no tiene un proyecto, puede [crear uno nuevo](./create-new-projects.md).

## <a name="publish-to-folder"></a>Publicación en carpeta

Con Visual Studio para Mac, puede publicar proyectos de .NET Core en una carpeta mediante la herramienta Publicar. Después de publicar en una carpeta, puede transferir los archivos a otro entorno. Para publicar en una carpeta, siga estos pasos.

 1. En la ventana de la solución, haga clic con el botón derecho en el proyecto y elija **Publicar**.

    ![Menú contextual Publicar](media/publish-context-menu.png)

 2. Si ya había publicado este proyecto, verá el perfil de publicación en el menú. Seleccione ese perfil de publicación para iniciar el proceso de publicación.

 3. Para publicar este proyecto en una carpeta por primera vez, seleccione **Publicar en carpeta**.

    ![Menú contextual Publicar en carpeta](media/publish-to-folder-context-menu.png)

 4. Aparece el cuadro de diálogo **Publicar en carpeta**. En este cuadro de diálogo se puede personalizar la carpeta donde se va a publicar el proyecto. Puede usar el botón **Examinar** para hacerlo o pegar una ruta de acceso.

 5. Después de hacer clic en **Publicar**, suceden varias cosas. Primero se crea un perfil de publicación. Un perfil de publicación es un archivo MSBuild que se importa en el proyecto durante el proceso de publicación. Contiene las propiedades que se usan durante el proceso de publicación. Estos archivos se almacenan en `Properties/PublishProfiles` y tienen la extensión `.pubxml`. Después, se inicia el proceso de publicación. Puede supervisar el progreso en la barra de estado de Visual Studio para Mac.

    ![Barra de estado del IDE con el estado de publicación](media/publish-to-folder-status-bar.png)

 6. Cuando la publicación se completa correctamente, se abre una ventana de Finder que lleva a la carpeta de publicación. Ahora que ya se ha creado un perfil de publicación, se mostrará en el menú contextual de Publicar.

    ![Menú contextual Publicar con perfil de carpeta](media/publish-context-menu-with-folder-profile.png)

 7. Para publicar el proyecto de nuevo con la misma configuración, puede hacer clic en el perfil en el menú contextual de Publicar.

## <a name="customize-publish-options"></a>Personalización de las opciones de publicación

Para cambiar el nombre del perfil de publicación (que se muestra en el menú contextual de publicación), cambie el archivo del perfil de publicación. Asegúrese de no cambiar la extensión del archivo (`.pubxml`).

Para cambiar la ruta de acceso de la carpeta de publicación, abra el perfil de publicación y edite el valor `publishUrl`.

Para cambiar la configuración de compilación que se está usando, cambie la propiedad `LastUsedBuildConfiguration` en el perfil de publicación.