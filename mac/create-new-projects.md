---
title: Creación de nuevos proyectos y soluciones
description: En este artículo se explica cómo crear proyectos y soluciones en Visual Studio para Mac
author: conceptdev
ms.author: crdun
ms.date: 05/23/2019
ms.assetid: 5880BB10-0A12-47E2-8A82-7A2D59C4D579
ms.openlocfilehash: 045d92365501b888e56ce4ae397331e597b5b33a
ms.sourcegitcommit: 51dad3e11d7580567673e0d426ab3b0a17584319
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/10/2019
ms.locfileid: "66820743"
---
# <a name="creating-a-new-project"></a>Crear un proyecto nuevo

## <a name="opening-the-project-creation-dialog"></a>Abrir el cuadro de diálogo de creación del proyecto

Hay varias maneras de crear un nuevo proyecto en Visual Studio para Mac. Cuando abra por primera vez Visual Studio para Mac, se mostrará la pantalla de bienvenida. Desde aquí puede elegir **New** que le llevará a la pantalla de creación del proyecto.

> [!TIP]
> Además, desde la pantalla de bienvenida también puede abrir y buscar, proyectos y soluciones recientes. También puede abrir proyectos recientes, vaya a la barra de menús y elegir **archivo > Soluciones recientes**

![Pantalla de bienvenida con crear nuevo proyecto](media/first-run-project.png)

Si Visual Studio para Mac ya está abierto con una solución cargada, puede crear una nueva solución, vaya a la barra de menús y elegir **archivo > nueva solución**. Crear una nueva solución de este modo se cerrará la solución que ya está cargada.

## <a name="creating-a-new-project-from-a-template"></a>Crear un nuevo proyecto a partir de una plantilla

El **nuevo proyecto** cuadro de diálogo, de forma predeterminada, mostrará las plantillas usadas recientemente ordenadas por *usados más recientemente*.

Si no desea usar una plantilla recientes, puede elegir en las categorías de la izquierda del cuadro de diálogo. Cada categoría contiene varias plantillas de proyecto para que pueda elegir. Al hacer clic en un tipo de proyecto le permite ver una descripción en el lado derecho de la pantalla.

![Pantalla de proyecto nuevo](media/project-creation-screen.png)

## <a name="configuring-your-new-project"></a>Configurar el nuevo proyecto

Una vez haya elegido una plantilla de proyecto, las siguientes pantallas le guiará por los pasos de configuración necesarios para configurar el proyecto; Esto puede variar según el tipo de proyecto.

Todos los proyectos requieren un nuevo proyecto, junto con una ubicación para almacenar los archivos. Si el proyecto forma parte de una solución nueva, en lugar de agregarlo a una solución existente, también será necesario un nombre de la solución.

Si lo desea, en esta fase también puede configurar las opciones de control de código fuente de Git. La imagen siguiente es un ejemplo del paso final de la configuración para un proyecto .NET Core:

![Configuración de un proyecto nuevo](media/configure-new-project.png)

## <a name="adding-additional-projects-to-a-solution"></a>Agregar proyectos adicionales a una solución

Puede agregar proyectos adicionales a una solución haciendo clic en la solución en el panel de solución y elegir cualquiera **Agregar > Agregar nuevo proyecto** o **Agregar > Agregar proyecto existente**.

Agregar un nuevo proyecto le llevará a través de la creación del proyecto, como se muestra en [configurar el nuevo proyecto](#configuring-your-new-project).

Optar por agregar un proyecto existente, podrá buscar un proyecto existente en el equipo y agregarlo a la solución.

## <a name="see-also"></a>Vea también

- [Crear soluciones y proyectos (Visual Studio en Windows)](/visualstudio/ide/creating-solutions-and-projects)