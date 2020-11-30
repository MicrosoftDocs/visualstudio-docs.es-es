---
title: Conexión a proyectos en Team Explorer
description: Aprenda a usar Team Explorer en Visual Studio para trabajar con los miembros del equipo en el desarrollo y la administración de proyectos.
ms.custom: SEO-VS-2020
ms.date: 11/17/2020
ms.topic: conceptual
ms.author: tglee
author: TerryGLee
ms.manager: jillfra
ms.openlocfilehash: fd482bd2225025b5cd8a14f0387e938626fad6d5
ms.sourcegitcommit: 66cda27b63c9b55782b1db223a6dbda9f8cabe13
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2020
ms.locfileid: "95006320"
---
# <a name="connect-to-projects-in-team-explorer"></a>Conexión a proyectos en Team Explorer

::: moniker range="vs-2017"

Use la ventana de la herramienta **Team Explorer** para coordinar los esfuerzos de código con otros miembros del equipo para desarrollar un proyecto y para administrar el trabajo que tiene asignado usted, su equipo o sus proyectos. **Team Explorer** conecta Visual Studio con repositorios de Git y GitHub, repositorios de Control de versiones de Team Foundation (TFVC) y proyectos hospedados en [Azure DevOps Services](/azure/devops/user-guide/what-is-azure-devops-services) o en una instancia local de [Azure DevOps Server](/azure/devops/index-all) (conocido anteriormente como TFS). Puede administrar código fuente, elementos de trabajo y compilaciones.

::: moniker-end

::: moniker range="vs-2019"

Puede usar la ventana de herramientas de **Team Explorer** para coordinar los trabajos de creación de código con otros miembros del equipo para desarrollar un proyecto, y para administrar el trabajo que le han asignado a usted y a su equipo, o sus proyectos.

> [!IMPORTANT]
> Con la versión reciente de Visual Studio 2019, [16.8](/visualstudio/releases/2019/release-notes/), la nueva experiencia de control de versiones de Git ahora está activada de forma predeterminada. Sin embargo, si prefiere seguir usando Team Explorer, vaya a **Herramientas** > **Opciones** > **Entorno** > **Características en versión preliminar** y, luego, active o desactive la casilla **New Git user experience** (Nueva experiencia de usuario de GIT). Para más información, consulte la página [Experiencia de Git en Visual Studio](git-with-visual-studio.md).

**Team Explorer** conecta Visual Studio con repositorios de Git y GitHub, repositorios de Control de versiones de Team Foundation (TFVC) y proyectos hospedados en [Azure DevOps Services](/azure/devops/user-guide/what-is-azure-devops-services) o en una instancia local de [Azure DevOps Server](/azure/devops/index-all) (conocido anteriormente como TFS). Puede administrar código fuente, elementos de trabajo y compilaciones.

::: moniker-end

![Página principal de Team Explorer en Visual Studio](media/team-explorer/team-explorer.png "Team Explorer: página principal en Visual Studio.")

::: moniker range="vs-2017"

> [!TIP]
> Si abre Visual Studio y no aparece **Team Explorer**, seleccione **Vista** > **Team Explorer** en la barra de menús para abrirlo **Ctrl**+ **&#92;** , **Ctrl**+**M**.

::: moniker-end

## <a name="connect-to-a-project-or-repository"></a>Conexión a un proyecto o repositorio

En la página **Conectar** se puede conectar a un proyecto o repositorio.

![Página Conectar en Team Explorer](media/team-explorer/connect.png "Team Explorer: página Conexiones en Visual Studio.")

Para conectarse a un proyecto:

1. Haga clic en el icono **Administrar conexiones** para abrir la página **Conectar**.

   ![Botón Administrar conexiones en Team Explorer](media/team-explorer/manage-connections.png "Team Explorer: botón Administrar conexiones en Visual Studio.")

1. En la página **Conectar**, seleccione **Administrar conexiones** > **Conectar a un proyecto**.

   ![Conectar a un proyecto en Team Explorer](media/team-explorer/connect-project.png "Team Explorer: opción Conectar a un proyecto en Visual Studio.")

> [!TIP]
> Si quiere abrir un proyecto desde un repositorio, vea [Abrir un proyecto desde un repositorio](../get-started/tutorial-open-project-from-repo.md). Si lo que quiere es crear un proyecto o agregar usuarios a un proyecto, vea [Creación de un proyecto (Azure DevOps)](/azure/devops/organizations/projects/create-project) y [Adición de usuarios a un proyecto o equipo (Azure DevOps)](/azure/devops/organizations/security/add-users-team-project).

## <a name="see-also"></a>Vea también

- [Nueva experiencia de Git en Visual Studio](git-with-visual-studio.md)
- [Tutorial: Abrir un proyecto desde un repositorio](../get-started/tutorial-open-project-from-repo.md)
- [Referencia de Team Explorer](reference/team-explorer-reference.md)
- [Conexión a un proyecto (Azure DevOps)](/azure/devops/organizations/projects/connect-to-projects)
- [Solución de problemas de conexión a un proyecto](/azure/devops/user-guide/troubleshoot-connection?view=azure-devops&preserve-view=true)
