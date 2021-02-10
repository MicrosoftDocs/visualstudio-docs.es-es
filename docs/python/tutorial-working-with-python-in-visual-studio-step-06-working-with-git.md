---
title: Paso 6 del tutorial de Python en Visual Studio, trabajar con Git
titleSuffix: ''
description: Paso 6 de un tutorial básico de Python en Visual Studio, que trata las características relacionadas con Git de Visual Studio.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: db5a8857a6b6610fdc60b05158379ef69995ddf3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920752"
---
# <a name="step-6-work-with-git"></a>Paso 6: Trabajar con Git

**Paso anterior: [Instalación de paquetes y administración del entorno de Python](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)**

Visual Studio proporciona integración directa con repositorios de Git locales y repositorios remotos en servicios como GitHub y Azure Repos. La integración incluye clonar un repositorio, confirmar los cambios y administrar ramas.

En este artículo se proporciona una introducción básica sobre la creación de un repositorio de Git local para un proyecto existente e información para familiarizarse con algunas características relacionadas con Git de Visual Studio.

1. Con un proyecto abierto en Visual Studio, como el proyecto del [paso anterior](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md), haga clic con el botón derecho en la solución y seleccione **Agregar solución al control de código fuente**. Visual Studio crea un repositorio de Git local que contiene el código del proyecto.

1. Cuando Visual Studio detecta que el proyecto se administra en un repositorio de Git, aparecen controles relacionados con Git en la esquina inferior derecha de la ventana de Visual Studio. Los controles muestran confirmaciones pendientes, cambios, el nombre del repositorio y la rama. Mantenga el puntero sobre los controles para ver más información.

    ![Se muestra información adicional cuando se mantiene el puntero sobre un control de Git en la ventana de Visual Studio](media/working-with-git-01.png)

1. Al crear un nuevo repositorio o seleccionar cualquiera de los controles de Git, Visual Studio abre la ventana **Team Explorer**. (Puede abrir la ventana en cualquier momento con el comando de menú **Ver** > **Team Explorer**). La ventana tiene tres paneles principales, entre los que puede cambiar mediante la lista desplegable del encabezado de **Team Explorer**. El panel **Sincronización** panel, que proporciona operaciones de publicación, también aparece cuando se selecciona el control de **inserción** (el icono de flecha arriba):

    ![Team Explorer en Visual Studio después de crear un repositorio local](media/working-with-git-02.png)

1. Seleccione **Cambios** (o el control de Git con el icono de lápiz) para revisar cambios sin confirmar y confirmarlos cuando quiera.

    ![Team Explorer en Visual Studio mostrando los cambios sin confirmar](media/working-with-git-03.png)

    Haga doble clic en un archivo en la lista **Cambios** para abrir una vista de diferencias para dicho archivo:

    ![Vista de diferencias para los cambios en un archivo](media/working-with-git-05.png)

1. Seleccione **Ramas** (o el control de Git con un nombre de rama) para examinar ramas y realizar operaciones de combinar y fusionar mediante cambio de base:

    ![Team Explorer en Visual Studio que muestra ramas](media/working-with-git-04.png)

1. Al seleccionar el control de Git con el nombre del repositorio (**CosineWave** en una imagen anterior), **Team Explorer** muestra una interfaz **Conectar** con la que puede cambiar rápidamente a otro repositorio por completo.

1. Cuando se usa un repositorio local, los cambios confirmados van directamente al repositorio. Si está conectado a un repositorio remoto, seleccione el encabezado desplegable en **Team Explorer**, elija **Sincronización** para cambiar a la sección **Sincronización** y trabaje con los comandos **pull** y **fetch** incluidos allí.

## <a name="go-deeper"></a>Profundizar un poco más

Para obtener un breve tutorial de creación de un proyecto desde un repositorio de Git remoto, vea [Inicio rápido: Clonación de un repositorio de código de Python en Visual Studio](quickstart-03-python-in-visual-studio-project-from-repository.md).

Para ver un tutorial mucho más completo, incluido el control de conflictos de combinación, la revisión de código con solicitudes de incorporación de cambios, la reorganización y la selección exclusiva de cambios entre ramas, consulte [Get Started with Git and Azure Repos](/azure/devops/repos/git/gitquickstart) (Introducción a Git y Azure Repos).

## <a name="tutorial-review"></a>Revisión del tutorial

Enhorabuena por completar este tutorial sobre Python en Visual Studio. En este tutorial ha aprendido a:

- Crear proyectos y ver el contenido de un proyecto.
- Usar el editor de código y ejecutar un proyecto.
- Usar la ventana **interactiva** para desarrollar nuevo código y copiar fácilmente ese código en el editor.
- Ejecutar el programa completado en el depurador de Visual Studio.
- Instalar paquetes y administrar entornos de Python.
- Trabajar con código en un repositorio de Git.

Desde aquí, explore los conceptos y las guías de procedimientos, incluidos los siguientes artículos:

- [Creación de una extensión de C++ para Python](working-with-c-cpp-python-in-visual-studio.md)
- [Publicación en Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [Generación de perfiles](profiling-python-code-in-visual-studio.md)
- [Pruebas unitarias](unit-testing-python-in-visual-studio.md)
