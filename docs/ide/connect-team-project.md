---
title: Conexión a proyectos en Team Explorer
description: Aprenda a usar Team Explorer en Visual Studio para trabajar con los miembros del equipo en el desarrollo y la administración de proyectos.
ms.custom: SEO-VS-2020
ms.date: 06/11/2021
ms.topic: conceptual
ms.author: tglee
author: TerryGLee
ms.manager: jillfra
monikerRange: <=vs-2019
ms.openlocfilehash: b45399f7a4115ce5946a67caca22ca92148e7434
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308251"
---
# <a name="connect-to-projects-in-team-explorer"></a>Conexión a proyectos en Team Explorer

::: moniker range="vs-2017"

Use la ventana de la herramienta **Team Explorer** para coordinar los esfuerzos de código con otros miembros del equipo para desarrollar un proyecto y para administrar el trabajo que tiene asignado usted, su equipo o sus proyectos. **Team Explorer** conecta Visual Studio con repositorios de Git y GitHub, repositorios de Control de versiones de Team Foundation (TFVC) y proyectos hospedados en [Azure DevOps Services](/azure/devops/user-guide/what-is-azure-devops-services) o en una instancia local de [Azure DevOps Server](/azure/devops/index-all) (conocido anteriormente como TFS). Puede administrar código fuente, elementos de trabajo y compilaciones.

::: moniker-end

::: moniker range="vs-2019"

Team Explorer conecta Visual Studio con repositorios de control de versiones de Team Foundation (TFVC) y con proyectos hospedados en [Azure DevOps Services](/azure/devops/user-guide/what-is-azure-devops-services) o en una instancia local de [Azure DevOps Server](/azure/devops/user-guide/about-azure-devops-services-tfs?view=azure-devops&preserve-view=true) (conocido anteriormente como TFS). Puede administrar código fuente, elementos de trabajo y compilaciones.

> [!IMPORTANT]
> Con la publicación de Visual Studio 2019, [**versión 16.8**](/visualstudio/releases/2019/release-notes-history), la nueva experiencia de control de versiones de Git está activada de forma predeterminada. Si quiere más información sobre la comparación con Team Explorer, consulte la página [**Comparación en paralelo de Git y Team Explorer**](../version-control/git-team-explorer-feature-comparison.md).
>
> Sin embargo, si prefiere seguir usando Team Explorer, vaya a **Herramientas** > **Opciones** > **Entorno** > **Características en versión preliminar** y, luego, active o desactive la casilla **New Git user experience** (Nueva experiencia de usuario de Git).

La forma de usar Team Explorer para conectarse a un proyecto depende de la versión de Visual Studio 2019 que use.

## <a name="in-version-168-and-later"></a>En la versión 16.8 y posterior

1. Abra Visual Studio 2019.

1. En la ventana de inicio, seleccione **Clonar un repositorio**.

   ![Captura de pantalla del cuadro de diálogo "Clonar un repositorio" en Visual Studio 2019, versión 16.8 y posteriores, para Azure DevOps](../ide/media/vs-2019/clone-repository.png)

1. En la sección **Examinar un repositorio**, seleccione **Azure DevOps**.

    ![Captura de pantalla de la sección "Examinar un repositorio" del cuadro de diálogo "Conectar a un proyecto" en Visual Studio 2019, versión 16.8 y posteriores](../ide/media/vs-2019/browse-repository-azure-devops.png)

1. Si se abre una ventana de inicio de sesión, inicie sesión en su cuenta.

1. En el cuadro de diálogo **Conectar a un proyecto**, seleccione el repositorio al que quiere conectarse y, después, haga clic en **Clonar**.

      ![Captura de pantalla del cuadro de diálogo "Conectar a un proyecto" que se genera en Visual Studio 2019, versión 16.8 y posteriores](../ide/media/vs-2019/connect-project-azure-devops.png)

      > [!TIP]
      > Si no ve una lista previamente rellenada de repositorios a los que conectarse, seleccione **Agregar una instancia de Azure DevOps Server** para escribir la dirección URL de un servidor. También es posible que vea el mensaje "No se han encontrado servidores", que incluye vínculos para agregar una instancia existente de Azure DevOps Server o crear una cuenta de Azure DevOps.

   Después, Visual Studio abre el **Explorador de soluciones** y muestra las carpetas y los archivos.

1. Seleccione la pestaña **Team Explorer** para ver las acciones de Azure DevOps.

      ![Captura de pantalla del cuadro de diálogo "Team Explorer" que se genera en Visual Studio 2019, versión 16.8 y posteriores](../ide/media/vs-2019/team-explorer-azure-devops.png)

## <a name="in-version-167-and-earlier"></a>En la versión 16.7 y anterior

1. Abra Visual Studio 2019.

1. En la ventana de inicio, seleccione **Clonar o extraer código del repositorio**.

   ![Captura de pantalla de la ventana "Crear un proyecto" en Visual Studio 2019, versión 16.7 y anteriores](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. En la sección **Examinar un repositorio**, seleccione **Azure DevOps**.

   ![Captura de pantalla de la sección "Examinar un repositorio" con la opción "Azure DevOps" en la ventana "Clonar o extraer código del repositorio" en Visual Studio 2019, versión 16.7 y anteriores](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Si se abre una ventana de inicio de sesión, inicie sesión en su cuenta.

1. En el cuadro de diálogo **Conectar a un proyecto**, seleccione el repositorio al que quiere conectarse y, después, haga clic en **Clonar**.

      ![Captura de pantalla del cuadro de diálogo "Conectar a un proyecto" que se genera en Visual Studio 2019, versión 16.7 y anteriores](../get-started/media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > El contenido del cuadro de lista depende de los repositorios de Azure DevOps a los que tiene acceso.

   Visual Studio abre **Team Explorer** y aparece una notificación cuando se completa la clonación.

     ![Captura de pantalla de la ventana "Team Explorer" que se muestra en Visual Studio 2019, versión 16.7 y anteriores, cuando se completa la clonación](../get-started/media/vs-2019/clone-complete-azure-devops.png)

1. Para ver los archivos y carpetas, seleccione el vínculo **Mostrar vista de carpeta**.

     ![Captura de pantalla de la sección "Soluciones" de la ventana "Team Explorer" en Visual Studio 2019, versión 16.7 y anteriores, una vez completada la clonación](../get-started/media/vs-2019/show-folder-view-azure-devops.png)

     Visual Studio abre el **Explorador de soluciones**.

1. Elija el vínculo **Soluciones y carpetas** para buscar un archivo de solución (específicamente, un archivo .sln).

      ![Captura de pantalla de la notificación de "Soluciones y carpetas" desde Team Explorer en Visual Studio 2019, versión 16.7 y anteriores](../get-started/media/open-proj-repo-solutions-folders.png)

   Si no hay ningún archivo de solución en el repositorio, aparecerá el mensaje "No se encontró ninguna solución&quot;. Sin embargo, puede hacer doble clic en cualquier archivo del menú de carpeta para abrirlo en el editor de código de Visual Studio.

::: moniker-end

::: moniker range=&quot;vs-2017&quot;

![Página principal de Team Explorer en Visual Studio](media/team-explorer/team-explorer.png &quot;Team Explorer: página principal en Visual Studio.")

> [!TIP]
> Si abre Visual Studio y no aparece **Team Explorer**, seleccione **Vista** > **Team Explorer** en la barra de menús para abrirlo **Ctrl**+ **&#92;** , **Ctrl**+**M**.

## <a name="connect-to-a-project-or-repository"></a>Conexión a un proyecto o repositorio

En la página **Conectar** se puede conectar a un proyecto o repositorio.

![Página Conectar en Team Explorer](media/team-explorer/connect.png "Team Explorer: página Conexiones en Visual Studio.")

Para conectarse a un proyecto:

1. Haga clic en el icono **Administrar conexiones** para abrir la página **Conectar**.

   ![Botón Administrar conexiones en Team Explorer](media/team-explorer/manage-connections.png "Team Explorer: botón Administrar conexiones en Visual Studio.")

1. En la página **Conectar**, elija **Administrar conexiones**>**Conectar a un proyecto**.

   ![Conectar a un proyecto en Team Explorer](media/team-explorer/connect-project.png "Team Explorer: opción Conectar a un proyecto en Visual Studio.")

> [!TIP]
> Si quiere abrir un proyecto desde un repositorio, vea [Abrir un proyecto desde un repositorio](../get-started/tutorial-open-project-from-repo-visual-studio-2017.md). Si lo que quiere es crear un proyecto o agregar usuarios a un proyecto, vea [Creación de un proyecto (Azure DevOps)](/azure/devops/organizations/projects/create-project) y [Adición de usuarios a un proyecto o equipo (Azure DevOps)](/azure/devops/organizations/security/add-users-team-project).

::: moniker-end

## <a name="see-also"></a>Vea también

- [Comparación de Git y Team Explorer en paralelo](git-team-explorer-feature-comparison.md)
- [Nueva experiencia de Git en Visual Studio](git-with-visual-studio.md)
- [Referencia de Team Explorer](reference/team-explorer-reference.md)
- [Conexión a un proyecto (Azure DevOps)](/azure/devops/organizations/projects/connect-to-projects)
- [Solución de problemas de conexión a un proyecto](/azure/devops/user-guide/troubleshoot-connection?view=azure-devops&preserve-view=true)
