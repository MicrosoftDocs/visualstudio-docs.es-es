---
title: Proyectos y soluciones
description: Este documento se proporciona información general sobre los proyectos y las soluciones de Visual Studio para Mac.
ms.topic: overview
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/09/2020
ms.assetid: 8254505D-D96E-48BD-8A5E-CF6A917897EA
ms.openlocfilehash: c52b8513937505b40d17f7cd9fc05d9cf6a47941
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493405"
---
# <a name="projects-and-solutions-in-visual-studio-for-mac"></a>Proyectos y soluciones en Visual Studio para Mac

En este artículo se proporciona información general sobre los conceptos de *proyecto* y *solución* de Visual Studio para Mac.

> [!NOTE] 
> Este tema se aplica a Visual Studio para Mac. En el caso de Visual Studio para Windows, vea [Soluciones y proyectos en Visual Studio](/visualstudio/ide/solutions-and-projects-in-visual-studio).

## <a name="projects"></a>Proyectos

Al crear una nueva aplicación, un sitio web, etc. en Visual Studio para Mac, se comienza con un proyecto. El proyecto contiene todos los archivos necesarios (código fuente, imágenes, archivos de datos, etc.) para compilar el archivo ejecutable, la biblioteca o el sitio web.

Un proyecto se define mediante un archivo (por ejemplo, `.csproj` para proyectos de C#) que contiene XML que define la jerarquía de carpetas y archivos, las rutas de acceso a los archivos y las configuraciones específicas del proyecto, como la de compilación.

Cuando Visual Studio para Mac carga un proyecto, la ventana de la solución usa el archivo de proyecto para mostrar los archivos y las carpetas del proyecto. Durante la compilación, MSBuild lee la configuración del archivo de proyecto para crear el archivo ejecutable.

## <a name="solutions"></a>Soluciones

Una *solución* es un contenedor que agrupa uno o más proyectos relacionados. Las soluciones se describen mediante un archivo de texto (extensión `.sln`) con su propio formato único; no están diseñadas para modificarse de forma manual.

## <a name="managing-projects-in-the-solution-window"></a>Administración de proyectos en la ventana de la solución

Una vez que un proyecto se ha creado o se ha cargado, puede usar la ventana de la solución para ver y administrar el proyecto o la solución y los archivos que contiene. En la siguiente ilustración se muestra la ventana de la solución con una solución de .NET Core que contiene dos proyectos:

![Solución de ejemplo con varios proyectos](media/solution-example.png)

Puede administrar las propiedades de proyectos y soluciones si hace doble clic en el nombre del proyecto o la solución o si hace clic con el botón derecho y selecciona **Opciones**.

Se proporciona más información sobre estas opciones en el artículo [Administrar propiedades de soluciones y proyectos](managing-solutions-and-project-properties.md).

## <a name="see-also"></a>Vea también

- [Soluciones y proyectos en Visual Studio (Windows)](/visualstudio/ide/solutions-and-projects-in-visual-studio)
