---
title: 'Tutorial: Apertura de un proyecto desde un repositorio en Visual Studio 2017'
description: Obtenga información sobre cómo abrir un proyecto en un repositorio de Git o de Azure DevOps mediante Visual Studio 2017.
ms.custom: get-started
ms.date: 01/25/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
monikerRange: vs-2017
ms.openlocfilehash: 97bfe7178d3bd744d1e441f8428cd38e8241b721
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951932"
---
# <a name="tutorial-open-a-project-from-a-repo-in-visual-studio-2017"></a>Tutorial: Apertura de un proyecto desde un repositorio en Visual Studio 2017

En este tutorial, usará Visual Studio 2017 para conectarse por primera vez a un repositorio y abrir un proyecto desde él.

> [!TIP]
> Hay una nueva manera totalmente integrada de conectarse a un repositorio de GitHub en [Visual Studio 2019](https://visualstudio.microsoft.com/downloads). Para obtener más información, consulte la página sobre la [**nueva experiencia de Git en Visual Studio 2019**](../ide/git-with-visual-studio.md?view=vs-2019&preserve-view=true).

## <a name="open-a-project-from-a-github-repo-by-using-visual-studio-2017"></a>Apertura de un proyecto desde un repositorio de GitHub mediante Visual Studio 2017

1. Abra Visual Studio 2017.

1. En la barra de menús superior, seleccione **Archivo** > **Abrir** > **Abrir desde el control de código fuente**.

   Se abre el panel **Team Explorer: conectar**.

    ![Ventana de Team Explorer dentro del IDE de Visual Studio](./media/open-proj-repo-team-explorer.png)

1. En la sección **Repositorios GIT locales**, seleccione **Clonar**.

    ![Elección de Clonar en la sección Repositorios GIT locales](./media/open-proj-repo-local-git-repo-clone.png)

1. En el cuadro que indica ***Enter the URL of a Git repo to clone** _ (Especifique la dirección URL del repositorio Git que se va a clonar), escriba o pegue la dirección URL del repositorio y presione _*ENTRAR**. (Es posible que se le solicite iniciar sesión en GitHub. Si es así, hágalo).

   Una vez que Visual Studio clona el repositorio, Team Explorer se cierra y se abre el Explorador de soluciones. Aparece un mensaje que indica *Haga clic en Soluciones y carpetas arriba para ver una lista de soluciones*. Elija **Soluciones y carpetas**.

   ![Elección de "Soluciones y carpetas" en el Explorador de soluciones](./media/open-proj-repo-github-solutions-folders.png)

1. Si hay disponible un archivo de solución, aparecerá en el menú emergente "Soluciones y carpetas". Elíjalo y Visual Studio abrirá la solución.

   ![Elija lo que quiere abrir en la lista desplegable del Explorador de soluciones](./media/open-proj-repo-github-solutions-folders-picker.png)

   Si no hay un archivo de solución (específicamente, un archivo .sln) en el repositorio, el menú desplegable dirá "No se encontró ninguna solución". Sin embargo, puede hacer doble clic en cualquier archivo del menú de carpeta para abrirlo en el editor de código de Visual Studio.

### <a name="review-your-work"></a>Revisión del trabajo

Vea la animación siguiente para comprobar el trabajo que ha realizado en la sección anterior.

   ![Animación de la apertura de un proyecto en el repositorio de GitHub mediante Visual Studio](./media/open-project-from-github.gif)

## <a name="open-a-project-from-an-azure-devops-repo-by-using-visual-studio-2017"></a>Apertura de un proyecto desde un repositorio de Azure DevOps mediante Visual Studio 2017

1. Abra Visual Studio 2017.

1. En la barra de menús superior, seleccione **Archivo** > **Abrir** > **Abrir desde el control de código fuente**.

   Se abre el panel **Team Explorer: conectar**.

    ![Ventana de Team Explorer dentro del IDE de Visual Studio](./media/open-proj-repo-team-explorer.png)

1. Existen dos maneras de conectarse al repositorio de Azure DevOps:

      - En la sección **Proveedores de servicio hospedado**, seleccione **Conectar…** .

        ![La sección Proveedores de servicio hospedado de la ventana Team Explorer dentro del IDE de Visual Studio](./media/open-proj-repo-azure-devops.png)

      - En la lista desplegable **Administrar conexiones**, seleccione **Conectar a un proyecto…** .

        ![La sección Administrar conexiones de la ventana Team Explorer dentro del IDE de Visual Studio](./media/open-proj-repo-azuredevops-manage-connections.png)

1. En el cuadro de diálogo **Conectar a un proyecto**, seleccione el repositorio al que quiere conectarse y, después, haga clic en **Clonar**.

      ![Cuadro de diálogo "Conectar a un proyecto" que se genera en Visual Studio](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > El contenido del cuadro de lista depende de los repositorios de Azure DevOps a los que tiene acceso.

1. Una vez que Visual Studio clona el repositorio, Team Explorer se cierra y se abre el Explorador de soluciones. Aparece un mensaje que indica *Haga clic en Soluciones y carpetas arriba para ver una lista de soluciones*. Elija **Soluciones y carpetas**.

      ![La notificación de "Soluciones y carpetas" desde Team Explorer en Visual Studio](./media/open-proj-repo-solutions-folders.png)

   Un archivo de solución (específicamente, un archivo .sln) aparecerá en el menú desplegable "Soluciones y carpetas". Elíjalo y Visual Studio abrirá la solución.

   Si no hay un archivo de solución en el repositorio, el menú desplegable dirá "No se encontró ninguna solución". Sin embargo, puede hacer doble clic en cualquier archivo del menú de carpeta para abrirlo en el editor de código de Visual Studio.

## <a name="next-steps"></a>Pasos siguientes

Si está listo para codificar con Visual Studio 2017, explore en profundidad cualquiera de los siguientes tutoriales específicos del lenguaje:

- [Tutoriales de Visual Studio | **C#**](./csharp/index.yml)
- [Tutoriales de Visual Studio | **Visual Basic**](./visual-basic/index.yml)
- [Tutoriales de Visual Studio | **C++**](/cpp/get-started/tutorial-console-cpp)
- [Tutoriales de Visual Studio | **Python**](../python/index.yml)
- [Tutoriales de Visual Studio | **JavaScript**, **TypeScript** y **Node.js**](../javascript/index.yml)

## <a name="see-also"></a>Consulte también

- [Azure DevOps Services: Get started with Azure Repos and Visual Studio](/azure/devops/repos/git/gitquickstart/) (Azure DevOps Services: Introducción a Azure Repos y Visual Studio)
- [Microsoft Learn: Introducción a Azure DevOps](/learn/modules/get-started-with-devops/)
- [Nueva experiencia de Git en Visual Studio 2019](../ide/git-with-visual-studio.md?view=vs-2019&preserve-view=true)
