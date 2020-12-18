---
title: Introducción a la extensibilidad de Abrir carpeta en Visual Studio | Microsoft Docs
ms.date: 02/21/2018
ms.topic: overview
ms.assetid: 94c3f8bf-1de3-40ea-aded-7f40c4b314c7
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 964b360806f6f834aa57c475d2117c124f2cf8af
ms.sourcegitcommit: 8a0d0f4c4910e2feb3bc7bd19e8f49629df78df5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/18/2020
ms.locfileid: "97668643"
---
# <a name="open-folder-extensibility"></a>Extensibilidad de Abrir carpeta

La característica [Abrir carpeta](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) permite a los usuarios abrir cualquier código base en Visual Studio sin necesidad de archivos de proyecto o de solución. Abrir carpeta proporciona las características que los usuarios esperan de Visual Studio, como las siguientes:

* Integración y búsqueda del Explorador de soluciones
* Uso de colores en el editor
* Navegación Ir a
* Búsqueda Buscar en archivos

Cuando se usa con cargas de trabajo como para el desarrollo con .NET y C++, los usuarios también obtienen:

* IntelliSense enriquecido
* Funcionalidad específica del lenguaje

Con Abrir carpeta, los creadores de extensiones pueden crear características enriquecidas para cualquier lenguaje. Hay API que admiten la compilación, depuración y búsqueda de símbolos para cualquier archivo en el código base de un usuario. Los extensores actuales pueden actualizar sus características de Visual Studio existentes para comprender el código sin el respaldo de proyectos o una solución.

## <a name="an-api-without-project-systems"></a>Una API sin sistemas de proyecto

Históricamente, Visual Studio solo ha entendido los archivos de una solución y sus proyectos mediante sistemas del proyecto. Un sistema del proyecto es responsable de la funcionalidad y las interacciones de los usuarios de un proyecto cargado. Comprende los archivos que contiene su proyecto, la representación visual del contenido del proyecto, las dependencias de otros proyectos y la modificación del archivo de proyecto subyacente. Otros componentes funcionan en nombre del usuario a través de estas jerarquías y funciones. No todos los códigos base se representan bien en una estructura de proyectos y soluciones. Los lenguajes de scripting y el código abierto escrito en C++ para Linux son buenos ejemplos. Con Abrir carpeta, Visual Studio proporciona a los usuarios una nueva forma de interactuar con el código fuente.

Las API de Abrir carpeta pertenecen al espacio de nombres `Microsoft.VisualStudio.Workspace.*` y están disponibles para que los extensores generen y consuman datos o acciones en torno a archivos de Abrir carpeta. Las extensiones pueden usar estas API para proporcionar funcionalidad para muchas áreas, como las siguientes:

- [Áreas de trabajo](workspaces.md): el punto de inicio de la extensibilidad de Abrir carpeta es el área de trabajo y sus API.
- [Contextos y acciones de archivo](workspace-file-contexts.md): inteligencia de código específica del archivo proporcionada a través de contextos de archivo.
- [Indexación](workspace-indexing.md): recopilación y conservación de datos sobre áreas de trabajo de Abrir carpeta.
- [Servicios de lenguaje](workspace-language-services.md): integración de servicios de lenguaje en áreas de trabajo de Abrir carpeta.
- [Compilación](workspace-build.md): compatibilidad con compilaciones para áreas de trabajo de Abrir carpeta.

Las características que usan los tipos siguientes tendrán que adoptar nuevas API para admitir Abrir carpeta:

- `IVsHierarchy`
- `IVsProject`
- `DTE`

## <a name="feedback-comments-issues"></a>comentarios, sugerencias e incidencias

Abrir carpeta y las API `Microsoft.VisualStudio.Workspace.*` están en fase de desarrollo activo. Si observa un comportamiento inesperado, vea los problemas conocidos de la versión de interés. [Developer Community](https://aka.ms/feedback/suggest?space=8) es el lugar recomendado para votar y crear cualquier incidencia. Para cada comentario, se recomienda una descripción detallada de la incidencia. Incluya la versión de Visual Studio para la que desarrolla, las API que usa (lo que ha implementado y aquello con lo que interactúe), el resultado esperado y el resultado real. Si es posible, incluya un volcado del proceso devenv.exe. Use el seguimiento de incidencias de GitHub para proporcionar comentarios sobre esto y documentación relacionada.

## <a name="next-steps"></a>Pasos siguientes

* [Áreas de trabajo](workspaces.md): obtenga información sobre la API de área de trabajo de Abrir carpeta.