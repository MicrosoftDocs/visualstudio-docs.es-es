---
title: 'Tutorial: Abrir un proyecto desde un repositorio'
description: Obtenga información sobre cómo abrir un proyecto en un repositorio GIT o de Azure DevOps mediante Visual Studio.
ms.custom: get-started
ms.date: 03/30/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 928e77c5c28b76570525b8ea9037cd0d0cef7f99
ms.sourcegitcommit: 509fc3a324b7748f96a072d0023572f8a645bffc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58857572"
---
# <a name="tutorial-open-a-project-from-a-repo"></a>Tutorial: Abrir un proyecto desde un repositorio

En este tutorial, usará Visual Studio para conectarse por primera vez a un repositorio y luego abrir un proyecto desde él.

::: moniker range="vs-2017"

Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) para instalarlo de forma gratuita.

::: moniker-end

::: moniker range="vs-2019"

Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) para instalarlo de forma gratuita.

::: moniker-end

## <a name="open-a-project-from-a-github-repo"></a>Apertura de un proyecto desde un repositorio de GitHub

::: moniker range="vs-2017"

1. Abra Visual Studio 2017.

1. En la barra de menús superior, elija **Archivo** > **Abrir** > **Abrir desde el control de código fuente**.

   Se abre el panel **Team Explorer: conectar**.

    ![Ventana de Team Explorer dentro del IDE de Visual Studio](./media/open-proj-repo-team-explorer.png)

1. En la sección **Repositorios GIT locales**, elija **Clonar**.

    ![Elección de Clonar en la sección Repositorios GIT locales](./media/open-proj-repo-local-git-repo-clone.png)

1. En el cuadro que indica ***Especifique la dirección URL del repositorio GIT que se va a clonar***, escriba o pegue la dirección URL del repositorio y presione **ENTRAR**. (Es posible que se le solicite iniciar sesión en GitHub. Si es así, hágalo).

   Una vez que Visual Studio clona el repositorio, Team Explorer se cierra y se abre el Explorador de soluciones. Aparece un mensaje que indica *Haga clic en Soluciones y carpetas arriba para ver una lista de soluciones*. Elija **Soluciones y carpetas**.

   ![Elección de "Soluciones y carpetas" en el Explorador de soluciones](./media/open-proj-repo-github-solutions-folders.png)

1. Si hay disponible un archivo de solución, aparecerá en el menú emergente "Soluciones y carpetas". Elíjalo y Visual Studio abrirá la solución.

   ![Elija lo que quiere abrir en la lista desplegable del Explorador de soluciones](./media/open-proj-repo-github-solutions-folders-picker.png)

   Si no hay un archivo de solución (específicamente, un archivo .sln) en el repositorio, el menú desplegable dirá "No se encontró ninguna solución". Sin embargo, puede hacer doble clic en cualquier archivo del menú de carpeta para abrirlo en el editor de código de Visual Studio.

### <a name="review-your-work"></a>Revisión del trabajo

Vea la animación siguiente para comprobar el trabajo que ha realizado en la sección anterior.

   ![Animación de la apertura de un proyecto en el repositorio de GitHub mediante Visual Studio](./media/open-project-from-github.gif)

::: moniker-end

::: moniker range="vs-2019"

1. Abra Visual Studio 2019.

1. En la ventana de inicio, elija **Clonar o desproteger código**.

   ![Visualización de la ventana "Crear un proyecto"](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. Especifique o escriba la ubicación del repositorio y, luego, elija **Clonar**.

   ![Visualización de la ventana "Clonar o desproteger código"](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Visual Studio abre el proyecto desde el repositorio.

1. Si hay disponible un archivo de solución, aparecerá en el menú emergente "Soluciones y carpetas". Elíjalo y Visual Studio abrirá la solución.

   ![Elija lo que quiere abrir en la lista desplegable del Explorador de soluciones](./media/open-proj-repo-github-solutions-folders-picker.png)

   Si no hay un archivo de solución (específicamente, un archivo .sln) en el repositorio, el menú desplegable dirá "No se encontró ninguna solución". Sin embargo, puede hacer doble clic en cualquier archivo del menú de carpeta para abrirlo en el editor de código de Visual Studio.

::: moniker-end

## <a name="open-a-project-from-an-azure-devops-repo"></a>Apertura de un proyecto desde un repositorio de Azure DevOps

::: moniker range="vs-2017"

1. Abra Visual Studio 2017.

1. En la barra de menús superior, elija **Archivo** > **Abrir** > **Abrir desde el control de código fuente**.

   Se abre el panel **Team Explorer: conectar**.

    ![Ventana de Team Explorer dentro del IDE de Visual Studio](./media/open-proj-repo-team-explorer.png)

1. Existen dos maneras de conectarse al repositorio de Azure DevOps:

      - En la sección **Proveedores de servicio hospedado**, elija **Conectar…**.

        ![La sección Proveedores de servicio hospedado de la ventana Team Explorer dentro del IDE de Visual Studio](./media/open-proj-repo-azure-devops.png)

      - En la lista desplegable **Administrar conexiones**, elija **Conectar a un proyecto…**.

        ![La sección Administrar conexiones de la ventana Team Explorer dentro del IDE de Visual Studio](./media/open-proj-repo-azuredevops-manage-connections.png)

1. En el cuadro de diálogo **Conectar a un proyecto**, elija el repositorio al que quiere conectarse y, luego, seleccione **Clonar**.

      ![El cuadro de diálogo "Conectar a un proyecto" que se genera desde Visual Studio](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > El contenido del cuadro de lista depende de los repositorios de Azure DevOps a los que tiene acceso.

1. Una vez que Visual Studio clona el repositorio, Team Explorer se cierra y se abre el Explorador de soluciones. Aparece un mensaje que indica *Haga clic en Soluciones y carpetas arriba para ver una lista de soluciones*. Elija **Soluciones y carpetas**.

      ![La notificación de "Soluciones y carpetas" desde Team Explorer en Visual Studio](./media/open-proj-repo-solutions-folders.png)

   Un archivo de solución (específicamente, un archivo .sln) aparecerá en el menú desplegable "Soluciones y carpetas". Elíjalo y Visual Studio abrirá la solución.

   Si no hay un archivo de solución en el repositorio, el menú desplegable dirá "No se encontró ninguna solución". Sin embargo, puede hacer doble clic en cualquier archivo del menú de carpeta para abrirlo en el editor de código de Visual Studio.

::: moniker-end

::: moniker range="vs-2019"

1. Abra Visual Studio 2019.

1. En la ventana de inicio, elija **Clonar o desproteger código**.

   ![Visualización de la ventana "Crear un proyecto"](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. En la sección **Examinar un repositorio**, elija **Azure DevOps**.

   ![Visualización de la ventana "Clonar o desproteger código"](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Si se abre una ventana de inicio de sesión, inicie sesión en su cuenta.

1. En el cuadro de diálogo **Conectar a un proyecto**, elija el repositorio al que quiere conectarse y, luego, seleccione **Clonar**.

      ![El cuadro de diálogo "Conectar a un proyecto" que se genera desde Visual Studio](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > El contenido del cuadro de lista depende de los repositorios de Azure DevOps a los que tiene acceso.

   Visual Studio abre **Team Explorer** y aparece una notificación cuando se completa la clonación.

     ![Ventana Team Explorer de Visual Studio cuando se completa la clonación](./media/vs-2019/clone-complete-azure-devops.png)

1. Para ver los archivos y carpetas, elija el vínculo **Mostrar vista de carpeta**.

     ![Sección Soluciones de la ventana Team Explorer de Visual Studio cuando se completa la clonación](./media/vs-2019/show-folder-view-azure-devops.png)

     Visual Studio abre el **Explorador de soluciones**.

1. Elija el vínculo **Soluciones y carpetas** para buscar un archivo de solución (específicamente, un archivo .sln).

      ![La notificación de "Soluciones y carpetas" desde Team Explorer en Visual Studio](./media/open-proj-repo-solutions-folders.png)

   Si no hay ningún archivo de solución en el repositorio, aparecerá un mensaje "No se encontró ninguna solución". Sin embargo, puede hacer doble clic en cualquier archivo del menú de carpeta para abrirlo en el editor de código de Visual Studio.

::: moniker-end

## <a name="next-steps"></a>Pasos siguientes

Si está listo para codificar con Visual Studio, explore en profundidad cualquiera de los siguientes tutoriales específicos del lenguaje:

- [Tutoriales de Visual Studio | **C#**](./csharp/index.yml)
- [Tutoriales de Visual Studio | **Visual Basic**](./visual-basic/index.yml)
- [Tutoriales de Visual Studio | **C++**](/cpp/get-started/)
- [Tutoriales de Visual Studio | **Python**](/visualstudio/python/)
- [Tutoriales de Visual Studio | **JavaScript**, **TypeScript** y **Node.js**](/visualstudio/javascript/)

## <a name="see-also"></a>Vea también

- [Azure DevOps Services: Get started with Azure Repos and Visual Studio (Azure DevOps Services: Introducción a Azure Repos y Visual Studio)](/azure/devops/repos/git/gitquickstart/)
- [Microsoft Learn: Introducción a Azure DevOps](/learn/modules/get-started-with-devops/)