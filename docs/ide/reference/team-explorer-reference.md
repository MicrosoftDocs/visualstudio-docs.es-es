---
title: Referencia de Team Explorer
ms.date: 12/04/2018
ms.topic: reference
ms.author: kaelli
author: KathrynEE
ms.manager: jillfra
ms.openlocfilehash: 6a7c1e9d0f5e8b8ef48a033d58038818d2d620e5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62945095"
---
# <a name="team-explorer-reference"></a>Referencia de Team Explorer

Este artículo contiene vínculos a artículos de Azure DevOps sobre las distintas funciones de **Team Explorer**.

Use la ventana de la herramienta **Team Explorer** para coordinar los esfuerzos de código con otros miembros del equipo para desarrollar un proyecto y para administrar el trabajo que tiene asignado usted, su equipo o sus proyectos. **Team Explorer** conecta Visual Studio con repositorios de Git y GitHub, repositorios de Control de versiones de Team Foundation (TFVC) y proyectos hospedados en [Azure DevOps Services](/azure/devops/user-guide/what-is-azure-devops-services) o en una instancia local de [Azure DevOps Server](/tfs/index) (conocido anteriormente como TFS). Puede administrar código fuente, elementos de trabajo y compilaciones.

## <a name="home-page"></a>página principal

Después de [conectarse a un proyecto](../connect-team-project.md) en **Team Explorer**, los vínculos siguientes están disponibles en la sección **Proyecto**:

- [Clonar repositorio](/azure/devops/repos/git/clone)
- [Portal web](/azure/devops/project/navigation/index)
- [Panel de tareas](/azure/devops/boards/sprints/task-board)

La página **Inicio** tiene otras funciones en función de si está conectado a un repositorio de [Git](/azure/devops/repos/git/gitquickstart?view=vsts&tabs=visual-studio) o de [Control de versiones de Team Foundation (TFVC)](/azure/devops/repos/tfvc/overview).

> [!TIP]
> Para obtener una comparación de los dos sistemas de control de versiones, vea [Choose the right version control for your project (Azure DevOps)](/azure/devops/repos/tfvc/comparison-git-tfvc) [Elección del control de versiones adecuado para el proyecto (Azure DevOps)].

| Página **Inicio** con Git | Página **Inicio** con TFVC |
| - | - |
| ![Página principal de Team Explorer con Git en Visual Studio 2019](media/team-explorer-reference/team-explorer-git.png) | ![Página principal de Team Explorer con TFVC en Visual Studio](media/team-explorer-reference/team-explorer-tfvc.png) |

## <a name="changes-page-git"></a>Página Cambios (Git)

Vea [Save work with commits](/azure/devops/repos/git/commits) (Guardar el trabajo con confirmaciones).

## <a name="branches-page-git"></a>Página de bifurcaciones (Git)

Vea [Create work in branches](/azure/devops/repos/git/branches) (Creación de trabajo en bifurcaciones).

## <a name="pull-requests-page-git"></a>Página de solicitudes de incorporación de cambios (Git)

Vea [Review code with pull requests](/azure/devops/repos/git/pullrequest) (Revisión del código con las solicitudes de incorporación de cambios).

## <a name="sync-page-git"></a>Página de sincronización (Git)

Vea [Update code with fetch and pull](/azure/devops/repos/git/pulling) (Actualización del código con buscar y extraer).

## <a name="tags-page-git"></a>Página de etiquetas (Git)

Vea [Work with Git tags](/azure/devops/repos/git/git-tags) (Trabajo con etiquetas de Git).

## <a name="my-work-page-tfvc"></a>Página Mi trabajo (TFVC)

Vea [Suspend/resume work](/azure/devops/repos/tfvc/suspend-your-work-manage-your-shelvesets) (Suspensión y reanudación del trabajo) y [Code review](/azure/devops/repos/tfvc/day-life-alm-developer-suspend-work-fix-bug-conduct-code-review) (Revisión del código).

## <a name="pending-changes-page-tfvc"></a>Página de cambios pendientes (TFVC)

Vea [Manage pending changes](/azure/devops/repos/tfvc/develop-code-manage-pending-changes) (Administración de los cambios pendientes), [Find shelvesets](/azure/devops/repos/tfvc/suspend-your-work-manage-your-shelvesets) (Búsqueda de conjuntos de cambios agregados pendientes de confirmación) y [Resolve conflicts](/azure/devops/repos/tfvc/resolve-team-foundation-version-control-conflicts) (Resolución de conflictos).

## <a name="source-control-explorer-page-tfvc"></a>Página Explorador de control de código fuente (TFVC)

Vea [Add/view files and folders](/azure/devops/repos/tfvc/add-files-server) (Adición y visualización de archivos y carpetas).

## <a name="work-items-page"></a>Página Elementos de trabajo

La página **Elementos de trabajo** permite ver las consultas de [elemento de trabajo](/azure/devops/boards/work-items/about-work-items). Vea:

- [Add work items](/azure/devops/boards/backlogs/add-work-items) (Adición de elementos de trabajo)
- [Use the query editor to list and manage queries](/azure/devops/boards/queries/using-queries) (Uso del editor de consultas para enumerar y administrar consultas)
- [Organize query folders and set query permissions](/azure/devops/boards/queries/set-query-permissions) (Organización de las carpetas de consulta y establecimiento de permisos de consulta)
- [Open query in Excel](/azure/devops/boards/backlogs/office/bulk-add-modify-work-items-excel) (Apertura de una consulta en Excel)
- [Open query in Project](/azure/devops/boards/backlogs/office/create-your-backlog-tasks-using-project) (Apertura de una consulta en Project)
- [Email query results list using Outlook](/azure/devops/boards/queries/share-plans) (Envío por correo electrónico de los resultados de la consulta con Outlook).
- [Create reports from query in Excel](/azure/devops/report/excel/create-status-and-trend-excel-reports) (Creación de informes a partir de una consulta en Excel) (solo TFS)

::: moniker range=">= vs-2019"

> [!NOTE]
> Hay una nueva [experiencia de elementos de trabajo](/azure/devops/boards/work-items/set-work-item-experience-vs) en Visual Studio 2019. Para obtener información sobre cómo ver los elementos de trabajo en Visual Studio 2019, vea [View and add work items](/azure/devops/boards/work-items/view-add-work-items) (Ver y agregar elementos de trabajo).

::: moniker-end

## <a name="builds-page"></a>Página Compilaciones

La página **Compilaciones** permite ver las definiciones de compilación para el proyecto.

Vea:

- [Create build pipelines](/azure/devops/pipelines/tasks/index) (Creación de canalizaciones de compilación)
- [View and manage builds](/azure/devops/pipelines/overview) (Supervisión y administración de compilaciones)
- [Manage the build queue](/azure/devops/pipelines/agents/pools-queues) (Administración de la cola de compilación)
- [Install continuous delivery (CD) tools for Visual Studio](/azure/devops/pipelines/apps/cd/azure/aspnet-core-to-acr#install-continuous-delivery-cd-tools-for-visual-studio-2017) (Instalación de herramientas de entrega continua (CD) para Visual Studio)
- [Configure and execute continuous delivery (CD) for your app](/azure/devops/pipelines/apps/cd/azure/aspnet-core-to-acr#configure-and-execute-continuous-delivery-cd-for-your-app) (Configuración y ejecución de la entrega continua (CD) para la aplicación)

## <a name="settings-page"></a>Página Configuración

La página **Configuración** permite configurar las características administrativas de un proyecto o una colección de proyectos. Vea los artículos siguientes:

| Proyecto | Colección de proyectos | Otros |
| - | - | - |
| [Seguridad, Pertenencia a grupos](/azure/devops/organizations/security/set-project-collection-level-permissions)<br/>[Seguridad, Control de código fuente (TFVC)](/azure/devops/organizations/security/set-git-tfvc-repository-permissions)<br/>[Áreas de elementos de trabajo](/azure/devops/organizations/settings/set-area-paths)<br/>[Iteraciones de elementos de trabajo](/azure/devops/organizations/settings/set-iteration-paths-sprints)<br/>[Configuración del portal](/azure/devops/report/sharepoint-dashboards/configure-or-add-a-project-portal)<br/>[Alertas del proyecto](/azure/devops/notifications/howto-manage-team-notifications) | [Seguridad, Pertenencia a grupos](/azure/devops/organizations/security/set-project-collection-level-permissions)<br/>[Control de código fuente (TFVC)](/azure/devops/repos/tfvc/decide-between-using-local-server-workspace)<br/>[Administrador de plantillas de procesos](/azure/devops/boards/work-items/guidance/manage-process-templates) | [Configuración global de Git](/azure/devops/repos/git/git-config)<br/>[Configuración de repositorios de Git](/azure/devops/repos/git/git-config) |

## <a name="see-also"></a>Vea también

- [Connect to projects in Team Explorer](../../ide/connect-team-project.md) (Conexión a proyectos en Team Explorer)