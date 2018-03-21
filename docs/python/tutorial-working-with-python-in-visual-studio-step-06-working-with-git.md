---
title: 'Trabajo con Python en Visual Studio, paso 6: trabajo con Git | Microsoft Docs'
description: "Paso 6 de un tutorial básico para trabajar con Python dentro de Visual Studio, que trata las características relacionadas con Git de Visual Studio."
ms.custom: 
ms.date: 01/16/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: ef143862c56f07edc844874bbf71cd916ac9eabc
ms.sourcegitcommit: 39c525ec200c6c4ea94815567b3fad7ab14fb7b3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2018
---
# <a name="step-6-working-with-git"></a>Paso 6: Trabajar con Git

**Paso anterior: [ Instalación de paquetes y administración de entornos de Python](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)**

Visual Studio proporciona integración directa con repositorios de Git locales y los que residen en servicios como GitHub y Visual Studio Team Services. La integración incluye clonar un repositorio, confirmar los cambios y administrar ramas.

En este artículo se describe cómo crear un repositorio de Git local para un proyecto existente. Para ver un tutorial de creación de un proyecto desde un repositorio de Git remoto, vea [Inicio rápido: Clonar un repositorio de código de Python en Visual Studio](quickstart-03-python-in-visual-studio-project-from-repository.md).

1. Con un proyecto abierto en Visual Studio, como el proyecto del [paso anterior](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md), haga clic con el botón derecho en la solución y seleccione **Agregar solución al control de código fuente**. Visual Studio crea un repositorio de Git local que contiene el código del proyecto y muestra controles relacionados con Git en la parte inferior de la ventana de Visual Studio. Los controles muestran confirmaciones pendientes, cambios, el nombre del repositorio y la rama. Mantenga el puntero sobre los controles para ver más información.

  ![Se muestra información adicional cuando se mantiene el puntero sobre un control de Git en la ventana de Visual Studio](media/working-with-git-01.png)

1. La ventana **Team Explorer** también aparece con distintas opciones de Git disponibles al seleccionar el encabezado de repositorio. El panel **Sincronización**, tal y como aparece cuando se selecciona el encabezado **Insertar**, proporciona opciones para publicar en un repositorio remoto.

  ![Team Explorer en Visual Studio después de crear un repositorio local](media/working-with-git-02.png)

1. Seleccione **Cambios** para revisar cambios sin confirmar y confirmarlos cuando quiera.

  ![Team Explorer en Visual Studio mostrando los cambios sin confirmar](media/working-with-git-03.png)

1. Seleccione **Ramas** para examinar bifurcaciones y realizar operaciones de combinar y fusionar mediante cambio de base:

  ![Team Explorer en Visual Studio que muestra ramas](media/working-with-git-04.png)

1. Cuando se usa un repositorio local, los cambios confirmados van directamente al repositorio. Si está conectado a un repositorio remoto, seleccione el encabezado, elija **Sincronización** para cambiar a la sección **Sincronización** y trabaje con los comandos incluidos allí.

## <a name="going-deeper"></a>Mayor profundización

Para ver un tutorial más extenso sobre cómo trabajar con Git, vea [Share your code with Visual Studio 2017 and VSTS Git](/vsts/git/share-your-code-in-git-vs-2017) (Compartir su código con Visual Studio 2017 y VSTS Git).

## <a name="tutorial-review"></a>Revisión del tutorial

Enhorabuena por completar este tutorial sobre Python en Visual Studio. En este tutorial ha aprendido a:

- Crear proyectos y ver el contenido de un proyecto.
- Usar el editor de código y ejecutar un proyecto.
- Usar la ventana interactiva para desarrollar nuevo código y copiar fácilmente ese código en el editor.
- Ejecutar el programa completado en el depurador de Visual Studio.
- Instalación de paquetes y administración de entornos de Python
- Trabajar con código en un repositorio de Git

Desde aquí, explore los conceptos y las guías de procedimientos, incluidos los siguientes:

- [Creación de una extensión de C++ para Python](working-with-c-cpp-python-in-visual-studio.md)
- [Publicación en Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [Generación de perfiles](profiling-python-code-in-visual-studio.md)
- [Pruebas unitarias](unit-testing-python-in-visual-studio.md)
