---
title: Creación de nuevos proyectos y soluciones
description: En este artículo se explica cómo crear proyectos y soluciones en Visual Studio para Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/23/2019
ms.assetid: 5880BB10-0A12-47E2-8A82-7A2D59C4D579
ms.openlocfilehash: dbfc0d951524bb9ffbbd4a2366679cfc6ae41925
ms.sourcegitcommit: 7fbfb2a1d43ce72545096c635df2b04496b0be71
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/09/2019
ms.locfileid: "67693065"
---
# <a name="creating-a-new-project"></a>Crear un proyecto nuevo

## <a name="opening-the-project-creation-dialog"></a>Apertura del cuadro de diálogo Creación de proyecto

Hay varias maneras de crear un proyecto en Visual Studio para Mac. Al abrir por primera vez Visual Studio para Mac, se muestra la pantalla de inicio. Desde ahí se puede elegir **Nuevo**, que lleva a la pantalla Creación de proyecto.

> [!TIP]
> Además, desde la pantalla de inicio también se pueden abrir y buscar proyectos y soluciones recientes. También puede abrir proyectos recientes si va a la barra de menús y selecciona **Archivo > Soluciones recientes**

![Pantalla de inicio con Crear nuevo proyecto](media/first-run-project.png)

Si Visual Studio para Mac ya está abierto con una solución cargada, puede crear una nueva solución si va a la barra de menús y selecciona **Archivo > Nueva solución**. Al crear una nueva solución de este modo se cierra la solución que ya estaba cargada.

## <a name="creating-a-new-project-from-a-template"></a>Creación de un proyecto a partir de una plantilla

El cuadro de diálogo **Nuevo proyecto** muestra de forma predeterminada las plantillas usadas recientemente ordenadas por *Usadas recientemente*.

Si no quiere usar una plantilla reciente, puede seleccionar entre las categorías de la izquierda del cuadro de diálogo. Cada categoría contiene varias plantillas de proyecto entre las que elegir. Al hacer clic en un tipo de proyecto, se puede ver una descripción en el lado derecho de la pantalla.

![Pantalla Nuevo proyecto](media/project-creation-screen.png)

## <a name="configuring-your-new-project"></a>Configuración del nuevo proyecto

Una vez que se elige una plantilla de proyecto, las siguientes pantallas guían a lo largo de los pasos de configuración necesarios para configurar el proyecto; esto puede variar según el tipo de proyecto.

Todos los proyectos requieren un nuevo proyecto, además de una ubicación para almacenar los archivos. Si el proyecto forma parte de una solución nueva, en lugar de agregarse a una solución existente, también es necesario un nombre de solución.

Opcionalmente, en esta fase también puede configurar opciones de control de código fuente de Git. La imagen siguiente es un ejemplo del paso de configuración final de un proyecto de .NET Core:

![Configuración de un proyecto nuevo](media/configure-new-project.png)

## <a name="adding-additional-projects-to-a-solution"></a>Incorporación de proyectos adicionales a una solución

Puede agregar proyectos adicionales a una solución si hace clic con el botón derecho en la solución en el Panel de solución y selecciona **Agregar > Agregar nuevo proyecto** o **Agregar > Agregar proyecto existente**.

La incorporación de un nuevo proyecto lleva a través de la creación del proyecto, como se muestra en [Configuración del nuevo proyecto](#configuring-your-new-project).

Si opta por agregar un proyecto existente, puede buscar un proyecto existente en el equipo y agregarlo a la solución.

## <a name="see-also"></a>Vea también

- [Crear soluciones y proyectos (Visual Studio en Windows)](/visualstudio/ide/creating-solutions-and-projects)