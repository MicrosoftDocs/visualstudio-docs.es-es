---
title: Proyectos y soluciones
description: Este documento se proporciona información general sobre los proyectos y las soluciones de Visual Studio para Mac.
author: conceptdev
ms.author: crdun
ms.date: 05/23/2019
ms.assetid: 8254505D-D96E-48BD-8A5E-CF6A917897EA
ms.openlocfilehash: ec62e9c0b449f5f2aed568735c2a10d1f6634eed
ms.sourcegitcommit: 51dad3e11d7580567673e0d426ab3b0a17584319
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/10/2019
ms.locfileid: "66820961"
---
# <a name="projects-and-solutions-in-visual-studio-for-mac"></a>Proyectos y soluciones en Visual Studio para Mac

En este artículo proporciona información general sobre la *proyecto* y *solución* conceptos en Visual Studio para Mac.

> [!NOTE] 
> En este tema se aplica a Visual Studio para Mac. Para Visual Studio en Windows, consulte [proyectos y soluciones en Visual Studio](/visualstudio/ide/solutions-and-projects-in-visual-studio).

## <a name="projects"></a>Proyectos

Al crear una nueva aplicación, el sitio Web, etc. en Visual Studio para Mac, para empezar un proyecto. El proyecto contiene todos los archivos necesarios (código fuente, imágenes, archivos de datos, etc.) que son necesarios para compilar el archivo ejecutable, biblioteca o sitio Web.

Un proyecto se define mediante un archivo (por ejemplo, `.csproj` para C# proyectos) que contiene código xml que define el archivo y la jerarquía de carpetas, rutas de acceso a archivos y configuraciones específicas del proyecto, como la configuración de compilación.

Cuando se carga un proyecto de Visual Studio para Mac, el panel de solución utiliza el archivo de proyecto para mostrar los archivos y carpetas en el proyecto. Durante la compilación, MSBuild lee la configuración del archivo de proyecto para crear el ejecutable.

## <a name="solutions"></a>Soluciones

Un *solución* es un contenedor que agrupa junto uno o más proyectos relacionados. Las soluciones se describen mediante un archivo de texto (extensión `.sln`) con su propio formato único; no se está diseñada para editarse manualmente.

## <a name="managing-projects-in-the-solution-pad"></a>Administración de proyectos en el panel de solución

Una vez que se ha creado un proyecto o se ha cargado, puede usar para ver y administrar el proyecto o solución y los archivos contenidos en el panel de solución. La siguiente ilustración muestra el panel de solución con una solución .NET Core que contiene dos proyectos:

![Solución de ejemplo con varios proyectos](media/solution-example.png)

Puede administrar las propiedades de proyectos y soluciones hace doble clic en el nombre del proyecto o solución, o con el botón secundario y elegir **opciones**.

Se proporciona más información sobre estas opciones en el artículo [Administrar propiedades de soluciones y proyectos](managing-solutions-and-project-properties.md).

## <a name="see-also"></a>Vea también

- [Soluciones y proyectos en Visual Studio (Windows)](/visualstudio/ide/solutions-and-projects-in-visual-studio)
