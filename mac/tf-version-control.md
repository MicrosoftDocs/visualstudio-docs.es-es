---
title: Control de versiones TF
description: Conectarse a Team Foundation Server o Visual Studio Team Services con Control de versiones de Team Foundation.
author: asb3993
ms.author: amburns
ms.date: 05/03/2018
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.openlocfilehash: f892209faeb06ca703d28016457e9ba4ab86ccda
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="connecting-to-team-foundation-version-control"></a>Conectarse a Control de versiones de Team Foundation 

Visual Studio Team Services (VSTS) y Team Foundation Server (TFS) proporcionan dos modelos de control de versiones: Git, que es un control de versiones distribuido y Control de versiones de Team Foundation (TFVC), que es un control de versiones centralizado. Este artículo proporciona información general y un punto de partida para usar Control de versiones de Team Foundation con Visual Studio para Mac.

> [!NOTE]
> **Nota**: la compatibilidad con Control de versiones de Team Foundation está actualmente en vista previa y algunas funciones todavía no funcionan al completo. Hay más cambios pendientes.

## <a name="requirements"></a>Requisitos

* Visual Studio para Mac, versión 7.5 o posterior.
* Visual Studio Team Services o Team Foundation Server 2013 y posterior
* Un proyecto en Visual Studio Team Services o Team Foundation Server, configurado para que use Control de versiones de Team Foundation.

## <a name="installation"></a>Instalación

Desde dentro de Visual Studio para Mac, elija el menú **Visual Studio > Extensiones...**. Busque "Control de versiones de TF" e instale la extensión **Control de versiones de Team Foundation**. Reinicie el IDE cuando se le pida.

## <a name="using-the-add-in"></a>Usar el complemento

Una vez que la extensión está instalada, seleccione el menú **Control de versiones > TFS/VSTS > Connect to Team Foundation Version Control...** (Conectar a Control de versiones de Team Foundation...). 

![Agregar un servidor TFVC](media/tfvc-add-remove-server.png)


Elija entre Visual Studio Team Services o Team Foundation Server para comenzar:

![Conectar con un servidor TFVC](media/tfvc-choose-server-type.png)

Escriba sus credenciales: 

![Inicie sesión en un servidor TFVC](media/tfvc-login.png)

Después, elija los proyectos a los que quiere acceder: 

![Elegir proyectos](media/tfvc-choose-projects.png)

Para continuar, cierre los cuadros de diálogo y luego use el menú **Control de versiones > TFS/VSTS > Explorador de control de código fuente** para examinar el código fuente.

> [!WARNING]
> **Problema conocido**: en esta versión preliminar, la primera vez que abra el explorador de control de código fuente, tendrá que crear una nueva área de trabajo.

![Explorador de código fuente](media/tfvc-source-explorer.png)

En el explorador de código fuente puede examinar el código fuente en el servidor y realizar las siguientes acciones:

- Administrar áreas de trabajo (crear, editar o eliminar).
- Navegar entre la estructura del proyecto.
- Asignar proyectos.
- Obtener proyectos.
- Bloquear y desbloquear archivos.
- Cambiar nombre de archivos.
- Eliminar archivos.
- Agregar nuevo archivo.
- Desproteger.
- Proteger.
- Ver historial de cambios.
- Comparar cambios.

## <a name="creating-a-new-workspace"></a>Crear una nueva área de trabajo

En el explorador de control de código fuente, haga clic en el botón **Administrar áreas de trabajo**. 

![Administrar áreas de trabajo](media/tfvc-manage-workspaces.png)

Haga clic en **Agregar** para crear una nueva área de trabajo.

![Crear área de trabajo](media/tfvc-create-workspace.png)

Proporcione un nombre para el área de trabajo y, después, haga clic en **Add Working Folder** (Agregar carpeta de trabajo) para asignar el proyecto a una carpeta local en el equipo.

Cuando termine, haga clic en **Aceptar** y luego cierre el cuadro de diálogo Administrar áreas de trabajo. Ya está listo para obtener los archivos a través del editor de código de origen y empezar a trabajar.